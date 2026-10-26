# MoE Offload Profiling

用于保存 Ascend NPU 上 SGLang MoE offload/cache 的 profiling 数据及分析。仓库默认私有。

## 上传数据

优先将压缩包上传到本仓库的 Releases 附件，避免大文件进入 Git 历史。

1. 打开 Releases，进入对应日期的数据批次，点击 Edit。
2. 在附件区域上传 zip 或 tar.gz，保存更新。
3. 将 Release 链接及附件名称发给分析者。

建议命名：`20261026-a5-offload-rank0.zip`、`20261026-a5-baseline-rank0.zip`。这些仅为命名示例，请按实际设备与 rank 修改。保留原始 profiler 目录结构；多 rank 数据请标明 rank。

每批数据同时提供一份说明，包含：

- 代码仓库、分支和 commit。
- NPU 型号、卡数，以及 torch、torch_npu、CANN、MemFabric 版本。
- 启动命令与 offload 配置。
- 请求输入/输出 token 数、并发数、请求数。
- 采集工具与参数，采集是否覆盖启动、graph capture、prefill、decode。
- 对应 benchmark 结果；有关闭 offload 的对照数据时一并提供。

没有基线 trace 也可以先上传 offload 数据。不要上传访问令牌、密码或模型权重。

## 分析目标

分析设备算子耗时和调用次数、CPU 调度与同步、权重搬运、卡间通信、缓存管理开销及关键执行路径。将结论关联到代码，并区分直接证据与待验证推测。