# DM Kit

DM Kit作为UNIT的开源对话管理模块，可以无缝对接UNIT的理解能力，并赋予开发者多状态的复杂对话流程管理能力，还可以低成本对接外部知识库，迅速丰富话术信息量。

## 快速开始

## 测试环境

ubuntu 18.04
python 3.6

### 编译DM Kit

DM Kit基于[brpc](https://github.com/brpc/brpc)开发并提供HTTP服务，支持MacOS，Ubuntu，Centos等系统环境。在编译DM Kit之前，需要先安装依赖并下载编译brpc：

```bash
sh deps.sh [OS]
```

其中[OS]参数指定系统类型用于安装对应系统依赖，支持取值包括ubuntu、mac、centos。如果已手动安装依赖，则传入none。

使用cmake编译DM Kit：

```bash
mkdir _build && cd _build && cmake .. && make
```

### 运行示例bot

DM Kit提供了示例场景bot，在运行示例bot之前，需要在UNIT平台配置实现bot的理解能力：[示例场景](docs/demo_bots.md)

根据UNIT平台创建的bot id修改编译产出_build目录下的conf/app/products.json文件，在其中配置所创建bot id与对应场景DM Kit配置文件。例如，查询流量及续订场景，在UNIT平台创建bot id为12345，则对应的配置文件内容应为：

```JSON
{
    "default": {
        "12345": {
            "score": 1,
            "conf_path": "conf/app/demo/cellular_data.json"
        }
    }
}
```

在_build目录下运行DM Kit：

```bash
./dmkit
```

可以通过tools目录下的bot_emulator.py程序模拟与bot进行交互，使用方法为：

```bash
python bot_emulator.py [bot id] [access token]
```

### 更多文档

* [DM Kit快速上手](docs/tutorial.md)
* [可视化配置工具](docs/visual_tool.md)

## 如何贡献

* 提交issue可以是新需求也可以是bug，也可以是对某一个问题的讨论。
* 对于issues中的问题欢迎贡献并发起pull request。

## 讨论

* 提issue发出问题讨论，如果是问题选择类型为问题即可。
* 加入UNIT开发者讨论群。
