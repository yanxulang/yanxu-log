# 贡献指南

## 兼容原则

- 1.x 不删除公开入口或改变记录模式 v1 基础字段类型。
- 新处理器、采样器或集成字段必须说明所有权、错误和资源边界。
- 任何敏感数据功能都要覆盖大小写、嵌套列/典和自由文本限制。
- 文件行为必须在 Linux、macOS、Windows 的最低言序门禁中验证。

## 本地检查

从仓库根目录执行：

```sh
yanxu 包 .
yanxu 查 src/言录.yx
yanxu 试 tests --json
yanxu 兼容 tests --json
yanxu 兼容 examples --json
yanxu 兼容 benchmarks --json
yanxu 包 锁 .
yanxu 包 锁 --离线 .
yanxu 编 . -o /tmp/yanxu-log.yxb --release
```

还应对`src/`、`tests/`、`examples/`和`benchmarks/`中的每个`.yx`文卷执行格式与静态检查，并确认：

```sh
yanxu 文 src/言录.yx /tmp/API.md
cmp docs/API.md /tmp/API.md
```

## 测试要求

新功能至少覆盖正常、边界、无效输入、资源限制、树解释器和字节码路径。文件测试须删除临时文件；示例必须使用固定时间源或不把时间放入可观察结果。

性能变更应更新`benchmarks/`中的回归工作负载，但不要把跨机器耗时阈值写成正确性断言。

## 提交

每个可独立验证的功能单独提交。提交前检查差异中没有凭据、生产日志或个人数据，并保持生成 API 与源码一致。
