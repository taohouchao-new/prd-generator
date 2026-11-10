# prd-generator

通过拷问式访谈（grilling）把一句笼统需求澄清成标准 PRD 的 agent skill，面向甲方、开发、测试三方。

## 它做什么

两种模式，按输入自动判断：

- **生成模式**：设计树梳理待定决策 → 分轮拷问（每问编号 + 推荐答案 + 一行理由）→ 套模板成文 → 画流程图/泳道图 → 交付前硬性自查 → 保存。
- **评审模式**：对照自查清单逐条审查已有 PRD，输出分级问题清单（阻断/重要/建议），给修改建议不重写全文。

模板与自查的核心设计：

- 业务规则量化到含/不含端点的区间；术语表先行，全文一个概念一个名字
- 有状态流转的产品先填状态迁移矩阵（每格必须裁决），再从矩阵推导验收标准
- 每条量化规则配「成功侧 + 失败侧」双 AC，规则覆盖核对表无空行才算交付
- 防幻觉硬约束：正文规则只能引用已定义的功能、术语、状态词
- 7 维度自查清单：异常流程（14 类）/ 页面状态 / 交互 / 消息通知 / 权限，评审外部 PRD 时逐维输出「已覆盖 / 待补充 / 不适用」三态判定

## 安装

```bash
npx skills add taohouchao-new/prd-generator
```

或手动拷贝本目录到 `~/.agents/skills/prd-generator/`。

## 用法

本 skill 刻意设计为**手动触发**，防止随口一句需求被过度成文：

- 输入 `/prd-generator`（可带初始需求，如 `/prd-generator 我要做个会议室预约系统`）；
- 或口头明确请求："帮我写 PRD""审一下这份 PRD""帮我澄清需求"。

只丢一句笼统需求而未要求成文时，不会触发——正常对话推进，想要成文时再说。

## 致谢

- [mattpocock/skills](https://github.com/mattpocock/skills)（MIT）——拷问机制（设计树 / 轮次 / 前沿）借鉴自其中的 grilling skill，在 PRD 场景做了扩展（取值扫描、规则组合扫描）；
- [PmEvolution/prd-self-check-skill](https://github.com/PmEvolution/prd-self-check-skill)——`references/self-check/` 五份清单整理自其「产品经理 PRD 自查系列」，并补充了与本模板的衔接说明；
- create-prd（原始出处已不可考）——模板雏形来源。

## 许可证

[MIT](./LICENSE)
