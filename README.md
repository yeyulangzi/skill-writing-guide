# 高质量 AI Skill 编写规范指南

> 写给 AI Agent 用户的 Skill 编写手册 —— 基于对 **50+ 个已安装 Skill** 的系统扫描与标杆识别，抽象出可复用的产品模式与技术模式。

## 这是什么

AI 时代，Skill（技能包）是让 Agent 稳定输出高质量结果的关键杠杆。但绝大多数 Skill 是"凭感觉写的"——触发不准、指令含糊、流程走到一半就崩。

这份指南回答一个问题：**什么样的 Skill 才是好 Skill，以及怎么写出这样的 Skill。**

它不是理论框架，而是从 **TDD、systematic-debugging、verification-before-completion、subagent-driven-development、huashu-design** 等 8 个标杆 Skill 中逆向提炼出的实战方法论。

## 核心能力

### 1. 产品视角：3 个评价维度

不关心 Skill "写得好不好看"，关心 **Agent 用了之后结果好不好**：

- **🎯 需求满足度** — 执行结果对不对（baseline 对比：加 Skill 后完成率从 30% → 90%）
- **🧭 使用体验** — 执行过程顺不顺（触发精准、认知负荷低、纠错成本小）
- **🔀 流程引导充分性** — 复杂流程能否走到终点（闸门、异常路径、防提前终止）

### 2. 技术视角：5 个工程约束

- **Token 预算意识** — 频繁加载 < 200 词，通用 < 500 行
- **防取巧设计** — Iron Law / 借口-现实对照表 / Red Flags，预判 Agent 会钻的每一个空子
- **交叉引用不粗暴加载** — 语义引用代替 `@` 强制加载
- **计算卸载** — `scripts/` 执行时不进上下文，只拿 stdout
- **流程图仅用于非显然决策**

### 3. 13 个已验证的写作套路

从标杆 Skill 中反复出现的设计手法提炼，如：第一行喊死规矩、预判 AI 偷懒借口、"换乘地图"、规则附真实失败故事+成本对比、逻辑链论证代替审美洁癖……

### 4. 11 个工程实现技巧

把 AI 当对手来写、字越少越好、关键步骤设闸门、对错摆一起、预制组件硬性绑定、领域资产优先级金字塔、Reference 路由表加优先级标注……

### 5. 开箱即用的检查清单

- **Skill 创建检查清单** — RED（写失败测试）→ GREEN（写最小 Skill）→ REFACTOR（封堵漏洞），把 TDD 方法论搬到 Skill 开发上
- **反模式速查表** — description 泄露工作流、无 baseline 就发布、借口表凭空编造…… 13 个常见坑一次说清

## 目录结构

```
├── README.md                        # 本文件（项目介绍）
└── skill-writing-guide.md           # 指南正文（完整方法论）
```

## 适用人群

- 想给自己的 AI Agent（Claude / Copilot / Codex / 自建 Agent）编写高质量 Skill 的开发者
- 在 Skill 市场（如 superpowers）发布 Skill 的作者
- 想理解"好 Skill 长什么样"的 AI 产品经理

## 核心理念

> **好 Skill = 对抗性设计 × token 预算 × 数据驱动迭代**，三者缺一不可。
>
> **没有 baseline 数据的 Skill = 没有单元测试的代码** —— 你根本不知道它有没有用。

## License

MIT
