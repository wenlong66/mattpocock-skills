<p>
  <a href="https://www.aihero.dev/s/skills-newsletter">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skills-repo-dark_2x.png">
      <source media="(prefers-color-scheme: light)" srcset="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skill-repo-light_2x.png">
      <img alt="Skills" src="https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skill-repo-light_2x.png" width="369">
    </picture>
  </a>
</p>

# 面向真实工程师的 Skills

[![skills.sh](https://skills.sh/b/mattpocock/skills)](https://skills.sh/mattpocock/skills)

[English](./README.md)

这些是我每天用于真实工程工作的 Agent Skills，不是 vibe coding。

开发真实应用很难。GSD、BMAD、Spec-Kit 这类方法试图通过接管流程来帮你，但在接管的同时，它们也拿走了你的控制权，并让流程里的 bug 很难被解决。

这些 skills 被设计得很小、容易改造、也能组合使用。它们适用于任何模型，背后来自数十年的工程经验。你可以随意改造它们，把它们变成你自己的工具。祝你玩得开心。

如果你想跟进这些 skills 的更新，以及我创建的新 skills，可以加入我约 60,000 名开发者订阅的 newsletter：

[订阅 Newsletter](https://www.aihero.dev/s/skills-newsletter)

## 安装（30 秒完成）

插件会自动更新。[skills.sh](https://skills.sh/mattpocock/skills) 会把可编辑的 skill 文件复制到你的项目中，由你手动更新。每个 agent 请选择一种方式，同时安装两者会导致每个 skill 出现两份。

### 1. 获取 skills

<details>
<summary><strong>Claude Code</strong></summary>

```bash
claude plugin install mattpocock-skills@claude-plugins-official
```

默认自动更新。

</details>

<details>
<summary><strong>Codex</strong></summary>

```bash
codex plugin marketplace add mattpocock/skills
codex plugin add mattpocock-skills@mattpocock
```

启动时自动更新。

</details>

<details>
<summary><strong>GitHub Copilot</strong>（CLI 和 VS Code）</summary>

```bash
copilot plugin marketplace add mattpocock/skills
copilot plugin install mattpocock-skills@mattpocock
```

然后在 `~/.copilot/settings.json` 中添加以下配置，只需配置一次：

```json
{
  "extraKnownMarketplaces": {
    "mattpocock": { "source": { "source": "github", "repo": "mattpocock/skills" }, "autoUpdate": true }
  }
}
```

在 VS Code 中，运行 **Chat: Install Plugin From Source**，并输入 `https://github.com/mattpocock/skills`。插件每天自动更新。

</details>

<details>
<summary><strong>Gemini CLI</strong>（手动更新）</summary>

```bash
gemini skills install https://github.com/mattpocock/skills.git --path skills/engineering
gemini skills install https://github.com/mattpocock/skills.git --path skills/productivity
```

需要更新时，重新运行这两条命令。

</details>

<details>
<summary><strong>其他 agent，或需要可编辑文件的用户</strong>（手动更新）</summary>

```bash
npx skills@latest add mattpocock/skills -a <agent>  # cursor, opencode, devin, windsurf, amp, pi; omit -a to choose
```

`-a <agent>` 用于指定目标 agent；省略 `-a` 则由安装器提示选择。安装器询问要安装哪些 skills 时，请包含 `setup-matt-pocock-skills`。更新时运行 `npx skills@latest update`，并重新运行 `add` 来安装新增的 skills。

</details>

### 2. 运行 `/setup-matt-pocock-skills`

在你的 agent 中为每个 repo 运行一次。它会：

- 询问你要使用哪种 issue tracker（GitHub、GitLab、本地文件，或你描述的其他系统）
- 询问你在 triage tickets 时使用哪些标签（`/triage` 会使用这些标签）
- 询问你希望把创建的文档保存在哪里

### 3. 完成

现在可以开始使用了。

## 为什么这些 Skills 存在

我构建这些 skills，是为了修复我在 Claude Code、Codex 以及其他 coding agents 中看到的常见失败模式。

### #1：Agent 没有做出我想要的东西

> “No-one knows exactly what they want”
>
> David Thomas & Andrew Hunt, [The Pragmatic Programmer](https://www.amazon.co.uk/Pragmatic-Programmer-Anniversary-Journey-Mastery/dp/B0833F1T3V)

**问题**：软件开发中最常见的失败模式是对齐失败。你以为开发者理解了你想要什么，但当你看到做出来的东西时，才发现对方根本没有理解。

AI 时代也是一样。你和 agent 之间存在沟通鸿沟。修复方式是一次 **grilling session**，让 agent 针对你要构建的东西提出详细问题。

**解决方案**是使用：

- [`/grill-me`](./skills/productivity/grill-me/SKILL.md)：用于非代码场景
- [`/grill-with-docs`](./skills/engineering/grill-with-docs/SKILL.md)：与 [`/grill-me`](./skills/productivity/grill-me/SKILL.md) 类似，但带有更多能力（见下文）

这是我最受欢迎的 skills。它们会在你开始前帮助你和 agent 对齐，并深入思考你要做的改动。每次想改东西时都应该使用它们。

### #2：Agent 太啰嗦了

> With a ubiquitous language, conversations among developers and expressions of the code are all derived from the same domain model.
>
> Eric Evans, [Domain-Driven-Design](https://www.amazon.co.uk/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215)

**问题**：项目初期，开发者和业务专家通常说着不同的语言。

我在使用 agents 时也感受到同样的张力。Agents 通常被丢进一个项目，然后被要求边做边弄懂术语。于是它们会用 20 个词表达 1 个词就够的意思。

**解决方案**是共享语言。它是一份文档，帮助 agents 解码项目中使用的术语。

<details>
<summary>
示例
</summary>

这里有一个来自我的 `course-video-manager` repo 的[术语表](https://github.com/mattpocock/course-video-manager/blob/076a5a7a182db0fe1e62971dd7a68bcadf010f1c/CONTEXT.md)示例。链接固定到的历史提交早于这些 skills 的命名约定调整，因此文件当时仍叫 `CONTEXT.md`。哪一个更容易读？

- **之前**：“There's a problem when a lesson inside a section of a course is made 'real' (i.e. given a spot in the file system)”
- **之后**：“There's a problem with the materialization cascade”

这种简洁会在一次又一次 session 中持续带来收益。

</details>

这内置在 [`/grill-with-docs`](./skills/engineering/grill-with-docs/SKILL.md) 中。它是一次 grilling session，同时也帮助你和 AI 建立共享语言，并把难以解释的决策记录到 ADR 中。

很难形容这有多强大。它可能是这个 repo 中最酷的技巧。试试看，你会感受到。

> [!TIP]
> 共享语言除了减少啰嗦之外，还有很多好处：
>
> - **变量、函数和文件会以一致的方式命名**，并使用共享语言
> - 因此，agent **更容易浏览代码库**
> - Agent 也会 **花更少 token 思考**，因为它能使用更简洁的语言

### #3：代码跑不起来

> “Always take small, deliberate steps. The rate of feedback is your speed limit. Never take on a task that’s too big.”
>
> David Thomas & Andrew Hunt, [The Pragmatic Programmer](https://www.amazon.co.uk/Pragmatic-Programmer-Anniversary-Journey-Mastery/dp/B0833F1T3V)

**问题**：假设你和 agent 已经对齐了要构建什么。如果 agent 仍然产出糟糕代码，会发生什么？

这时就该看反馈循环了。如果没有关于代码实际运行情况的反馈，agent 就是在盲飞。

**解决方案**：你需要常规的一组反馈循环：静态类型、浏览器访问能力和自动化测试。

对自动化测试来说，红-绿-重构循环非常关键。也就是让 agent 先写失败测试，再修复测试。这能给 agent 持续、明确的反馈，并显著提高代码质量。

我构建了一个可以放进任何项目中的 **[`/tdd`](./skills/engineering/tdd/SKILL.md) skill**。它鼓励红-绿-重构，并提供大量关于好测试和坏测试的指导。

调试方面，我也构建了 **[`/diagnosing-bugs`](./skills/engineering/diagnosing-bugs/SKILL.md)**，把最佳调试实践组织成一个纪律化循环，每个阶段满足条件后才进入下一阶段。

### #4：我们造出了一个大泥球

> “Invest in the design of the system _every day_.”
>
> Kent Beck, [Extreme Programming Explained](https://www.amazon.co.uk/Extreme-Programming-Explained-Embrace-Change/dp/0321278658)

> “The best modules are deep. They allow a lot of functionality to be accessed through a simple interface.”
>
> John Ousterhout, [A Philosophy Of Software Design](https://www.amazon.co.uk/Philosophy-Software-Design-2nd/dp/173210221X)

**问题**：大多数由 agents 构建的应用都复杂且难以修改。因为 agents 能极大加速编码，它们也会加速软件熵增。代码库会以前所未有的速度变复杂。

**解决方案**是采用一种面向 AI 开发的全新激进方法：关心代码设计。

这内置在这些 skills 的每一层中：

- [`/to-spec`](./skills/engineering/to-spec/SKILL.md) 会在创建 spec 之前询问你将触碰哪些模块

关键是，[`/improve-codebase-architecture`](./skills/engineering/improve-codebase-architecture/SKILL.md) 会调查代码库中可以加深模块设计的机会，并把候选项交给你。我建议每隔几天就在代码库上运行一次。它做的是调查，而不是自动拯救代码库：面对真正老旧的代码库，它会找出值得改进的候选项，但不会替你理清所有混乱。

### 总结

软件工程基本功比以往任何时候都更重要。这些 skills 是我将这些基本功浓缩成可重复实践的最佳尝试，希望帮助你交付职业生涯中最好的应用。祝你使用愉快。

## 参考

这些 skills 按一个维度区分：谁可以调用它们。**用户调用型** skills 只能在你输入时触达（例如 `/grill-me`）；它们负责组织流程。**模型调用型** skills 可以由你调用，也可以在任务适配时由 agent 自动触达；它们承载可复用的工程纪律。用户调用型 skill 可以调用模型调用型 skill，但不能调用另一个用户调用型 skill。

### Engineering

我每天用于代码工作的 skills。

**用户调用型**

- **[ask-matt](./skills/engineering/ask-matt/SKILL.md)**：询问哪一个 skill 或流程适合当前情况。它是这个 repo 中用户调用型 skills 的路由器。
- **[grill-with-docs](./skills/engineering/grill-with-docs/SKILL.md)**：一次 grilling session，同时建立项目的领域模型，打磨术语，并内联更新 `GLOSSARY.md` 和 ADR。
- **[triage](./skills/engineering/triage/SKILL.md)**：通过一组 triage 角色的状态机推进 issues。
- **[improve-codebase-architecture](./skills/engineering/improve-codebase-architecture/SKILL.md)**：扫描代码库中可以加深模块设计的机会，以可视化 HTML 报告呈现，然后围绕你选择的机会进行 grilling。
- **[setup-matt-pocock-skills](./skills/engineering/setup-matt-pocock-skills/SKILL.md)**：为这些 engineering skills 配置当前 repo（issue tracker、triage labels、domain docs 布局）。使用其他 engineering skills 前，每个 repo 运行一次。
- **[to-spec](./skills/engineering/to-spec/SKILL.md)**：将当前对话转成 spec 并发布到 issue tracker。不做访谈，只综合已经讨论过的内容。
- **[to-tickets](./skills/engineering/to-tickets/SKILL.md)**：将任何 plan、spec 或 conversation 拆成一组 tracer-bullet tickets，每个 ticket 都声明其 blocking edges；这些依赖关系会写成本地文件中的文本，或真实 tracker 中的原生 blocking links。
- **[implement](./skills/engineering/implement/SKILL.md)**：构建 spec 或 tickets 描述的工作，在预先同意的 seams 上驱动 `/tdd`，并在提交前用 `/code-review` 收尾。
- **[implement-spec](./skills/engineering/implement-spec/SKILL.md)**：在一个集成分支上实现完整 spec。将 tickets 作为任务图处理，让实现子代理并发推进当前所有依赖已满足的任务，最后用 `/code-review` 收尾。
- **[wayfinder](./skills/engineering/wayfinder/SKILL.md)**：为一个大到单个 agent session 放不下的工作块做规划，在 issue tracker 上生成共享的决策 tickets 地图；逐个解决它们，直到通往目标的路线清晰。
- **[retro](./skills/engineering/retro/SKILL.md)**：在一次 session 结束后，按问题严重程度为 coding agent 的环境提出改进建议，涵盖代码导航、自动检查、编码规范、指导文件和工具。

**模型调用型**

- **[prototype](./skills/engineering/prototype/SKILL.md)**：构建一次性原型来回答设计问题：状态/逻辑问题用单个可分享的 HTML 文件，UI 探索则提供多个可在一个 route 中切换的明显不同方案。
- **[diagnosing-bugs](./skills/engineering/diagnosing-bugs/SKILL.md)**：面向困难 bug 和性能回退的纪律化诊断循环：建立能因当前 bug 而失败的反馈循环 → 最小化 → 假设 → 加 instrumentation → 修复 → 回归测试。
- **[research](./skills/engineering/research/SKILL.md)**：针对高可信一手来源调查问题，并把结果保存为 repo 中一份带引用的 Markdown 文件；以后台 agent 运行。
- **[tdd](./skills/engineering/tdd/SKILL.md)**：使用红-绿-重构循环进行测试驱动开发。按垂直切片构建功能或修复 bug。
- **[domain-modeling](./skills/engineering/domain-modeling/SKILL.md)**：主动建立和打磨项目的领域模型：根据 glossary 挑战术语，用边界场景进行压力测试，并内联更新 `GLOSSARY.md` 与 ADR。
- **[codebase-design](./skills/engineering/codebase-design/SKILL.md)**：用于设计深模块的共享纪律和词汇：通过小接口暴露大量行为，放在干净 seam 上，并可通过该接口测试。
- **[code-review](./skills/engineering/code-review/SKILL.md)**：对固定基准之后的 diff 做双轴 review：**Standards**（是否遵循 repo 代码标准和 Fowler smell baseline）与 **Spec**（是否忠实实现原始 issue/spec）；两轴作为并行 sub-agents 运行，互不污染。
- **[pr](./skills/engineering/pr/SKILL.md)**：规范 pull request 正文的结构：用最精简的可视化说明变更，提供证明其有效的前后对比证据，并评估合并风险，包括变更是难以撤回的单向门还是可回退的双向门，以及影响范围。
- **[wizard](./skills/engineering/wizard/SKILL.md)**：生成交互式 bash 向导，引导用户完成只有他们才能执行的步骤，例如配置基础设施、设置凭据或 CI secrets、操作陌生的第三方 dashboard，以及执行一次性迁移或切换。

### Productivity

通用工作流工具，不专属于代码。

**用户调用型**

- **[grill-me](./skills/productivity/grill-me/SKILL.md)**：对一个 plan 或 design 进行持续追问，直到决策树的每个分支都被解决。
- **[handoff](./skills/productivity/handoff/SKILL.md)**：将当前对话压缩成 handoff 文档，让另一个 agent 可以继续工作。
- **[teach](./skills/productivity/teach/SKILL.md)**：在多次 session 中教用户一个新 skill 或概念，并把当前目录作为有状态的教学工作区。
- **[to-questionnaire](./skills/productivity/to-questionnaire/SKILL.md)**：将无法独自回答的决策整理成 Markdown 问卷，供真正能回答的人异步填写或在会议中共同完成。它会追问问卷发给谁、需要对方提供什么，而不是追问决策本身。
- **[wait-what](./skills/productivity/wait-what/SKILL.md)**：当一条消息没有被理解时立即使用，让 agent 补上你缺失的上下文，用 `GLOSSARY.md` 的词汇和直白语言重新表达。

**模型调用型**

- **[grilling](./skills/productivity/grilling/SKILL.md)**：围绕 plan、decision 或 idea 持续访谈用户，直到决策树的每个分支都被解决。它是 `grill-me`、`grill-with-docs`、`triage`、`wayfinder` 和 `improve-codebase-architecture` 背后的可复用循环。
- **[writing-for-agents](./skills/productivity/writing-for-agents/SKILL.md)**：编写面向 agent 的文档，包括 skills、AGENTS.md、CLAUDE.md，以及 agent 通过指针访问的其他文档。
