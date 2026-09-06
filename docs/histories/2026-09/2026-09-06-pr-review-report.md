## 2026-09-06 | 任务：优化 PR 审查报告结构

**Links:** [执行计划](../../exec-plans/completed/2026-09-06-pr-review-report.md)

### 用户请求

改善复杂 PR 长回复的阅读体验，按已确认方案调整信息结构、Markdown 层级与复审表达。

### 变更

- 审查结论与行动前置；待处理旧评论优先，新发现随后；无需修改的线程后置简述。
- 解除固定英文栏目及背景句数要求，采用段内标签和按复杂度伸缩的报告。
- 同步根入口与 review 核心的语义去重规则，保留逐线程证据、实质回复及准确快照。
- 分离代码修复判断与线程 resolve 状态，明确失败、未知和计数口径。

### 设计意图

压缩重复结构而非证据。摘要可引用问题 ID，但每个问题的详细评估只有一个归属。
保持原有 checkout、最终刷新、权限及 resolve 守卫，不新增技能或独立模板文件。

### 验证

- review 与 review-pr 的 skill 校验通过；`git diff --check` 通过。
- Terra 完成五类合成报告试用：无问题、仅新问题、旧问题未修复、复审全修复、混合部分 resolve 失败。
- 首轮成稿发现行动索引排序、后置线程链接、权限字段和位置链接问题，已补充交付前检查。
- `python3 .agents/skills/review-pr/tests/test_review_threads.py -v`：18/18 通过。
- 混合报告修订复验通过：P1 索引前置、线程链接齐全、权限自然语言化；
  其余样例错误位置链接的修正方式已逐项核对。不把合成 resolve 写为本次真实动作。
- 未访问真实 PR、未运行 Xcode，未修改产品或子代理模型。

### 受影响文件

- `AGENTS.md`
- `.agents/skills/review/SKILL.md`
- `.agents/skills/review-pr/SKILL.md`
- 本任务执行计划与 history

### 后续事项

- 实际宿主中的长报告视觉效果仍需结合后续真实 review 反馈迭代。
