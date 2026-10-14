# 🤖 个人 Agent 技能库 (Cherry Studio Skills)

本仓库用于统一保存、版本备份与分发我在 **Cherry Studio** 及各类 AI 智能体（Agent）中日常使用的自定义 Skills（技能包）。

每个技能均包含标准的 `SKILL.md` 定义文件及配套模板、脚本，遵循通用 Agent 协议，支持在支持 Skill 机制的智能体平台中一键挂载与调用。

---

## 📑 技能目录速览

| 序号 | 技能标识 (Folder) | 中文名称 | 分类 | 核心用途与定位 |
| :--- | :--- | :--- | :--- | :--- |
| 01 | [`agent-butler`](./skills/agent-butler/) | **智能管家 / 总参谋长** | 流程编排 | 针对高复杂度多步骤任务进行整体拆解，调度并指派 Plan、Explore 等专职 Agent 协同完成。 |
| 02 | [`cherry-browser`](./skills/cherry-browser/) | **Cherry 内置浏览器控制** | 浏览与操作 | 直接操控 Cherry Studio 右侧原生浏览器界面，执行网页浏览、表单填写、自动截屏与交互调试。 |
| 03 | [`cherry-tool-guide`](./skills/cherry-tool-guide/) | **Cherry 工具环境指南** | 系统与环境 | 指导 Agent 如何正确调用 Cherry Studio 原生 MCP 工具及本地环境（Bun、uv、Python、Ripgrep 等）。 |
| 04 | [`find-skills`](./skills/find-skills/) | **技能发现与安装器** | 扩展与管理 | 自动在开源 Agent 生态中检索匹配的技能包，帮助用户发现并安装符合需求的新技能。 |
| 05 | [`grill-me`](./skills/grill-me/) | **方案压力测试 (深度诘问)** | 思考与评估 | 模拟严苛的面试官或资深架构师，对用户的方案、计划和设计进行连续追问，排查盲区与漏洞。 |
| 06 | [`grill-with-docs`](./skills/grill-with-docs/) | **方案诘问与文档沉淀** | 思考与评估 | 在进行高强度方案压力测试的同时，同步自动生成架构决策记录（ADR）和专业术语表（Glossary）。 |
| 07 | [`obsidian-cli`](./skills/obsidian-cli/) | **Obsidian 命令行控制** | 笔记与知识库 | 通过命令行直接操作正在运行的 Obsidian，支持创建、搜索笔记、管理任务与属性，及插件调试。 |
| 08 | [`obsidian-markdown`](./skills/obsidian-markdown/) | **Obsidian 双链笔记助手** | 笔记与知识库 | 专门用于编写符合 Obsidian 语法的 Markdown 笔记，支持双向链接（`[[]]`）、嵌入、Callout 标注框等。 |
| 09 | [`office-transform`](./skills/office-transform/) | **Office 文档提取与转换** | 办公效率 | 在不改动原文件前提下，从 Word、Excel、PPT、PDF 中结构化提取内容，并衍生转换成新文件。 |
| 10 | [`playwright-cli`](./skills/playwright-cli/) | **Playwright 网页自动化** | 网页自动化 | 基于 Playwright CLI 的端到端自动化测试与浏览器网页交互控制。 |
| 11 | [`ppt-master`](./skills/ppt-master/) | **PPT 演示文稿大师** | 办公效率 | AI 驱动的专业 PPT 生成与美化工作流，支持生成可编辑 PPTX、重构版面排版与设计美化。 |
| 12 | [`skill-creator`](./skills/skill-creator/) | **技能创造与评估器** | 开发者工具 | 专门用于创建新技能、优化已有技能的提示词（Prompt）与触发规则，并进行性能评测。 |
| 13 | [`skills-sh-5vgid4`](./skills/skills-sh-5vgid4/) (`humanizer-zh`) | **中文去 AI 味 / 自然语言润色** | 写作与编辑 | 消除中文文本中的空话、套话、模板化表达与生硬翻译腔，使文字更加干练自然、具有人类质感。 |
| 14 | [`web-browser`](./skills/web-browser/) | **Chrome 浏览器控制 (CDP)** | 网页自动化 | 基于 Chrome DevTools Protocol (CDP) 的底层浏览器自动化，支持无头（Headless）网页操作与调试。 |

---

## 🔍 各技能详细中文说明

### 1. `agent-butler` - 智能管家 / 总协调员
- **核心定位**：当用户提出的任务非常复杂，涉及多个阶段（调研、方案设计、编码、测试等）时，该技能充当高层调度器（Butler）。
- **主要能力**：
  - 将庞大复杂的用户需求拆解为逻辑自洽的子任务步骤。
  - 根据子任务性质自动委派给最合适的专业模型或 Agent（如负责架构规划的 `Plan`、负责大范围搜索的 `Explore`）。
- **触发场景**：用户要求“制定总体方案”、“帮我规划这个大项目”、需要跨领域多模型协同。

### 2. `cherry-browser` - Cherry Studio 内置浏览器交互
- **核心定位**：专为 Cherry Studio 用户打造的内置浏览器驱动技能。
- **主要能力**：
  - 操控 Cherry 界面右侧侧边栏展示的浏览器页面。
  - 支持访问指定 URL、点击页面元素、输入框键入、滚动查看及截屏捕获。
- **触发场景**：需要在 Cherry Studio 客户端内查看网页、测试前端界面或执行可视化操作。

### 3. `cherry-tool-guide` - Cherry 原生工具与环境路由指南
- **核心定位**：为 Agent 注入 Cherry Studio 底层能力的“使用说明书”。
- **主要能力**：
  - 规范 Agent 正确使用 Cherry 的 MCP 服务（包括内存管理、定时任务、消息渠道、知识库等）。
  - 指引 Agent 在本地执行脚本时优先使用轻量高效的环境（如 JS/TS 使用 `bun`，Python 使用 `uv`）。
- **触发场景**：Agent 内部机制调用，确保智能体不走弯路，充分发挥系统自带工具优势。

### 4. `find-skills` - 技能发现与自动检索
- **核心定位**：开放技能生态的导航员。
- **主要能力**：
  - 当用户提出某个通用场景的需求（如“能不能帮我抓取知乎回答”、“有没有处理音频的技能”），自动在市场中搜索已有的成熟 Skill。
  - 向用户推荐并协助安装最合适的外部技能。
- **触发场景**：询问“怎么做某件事”、“有没有相关的 Skill / 插件”。

### 5. `grill-me` - 方案压力测试与深度诘问
- **核心定位**：思维打磨与漏洞排查利器。
- **主要能力**：
  - 扮演一位极其挑剔、敏锐的资深专家或面试官。
  - 对用户提出的计划、方案或架构设计展开多轮连续追问与压力测试，逼出方案中所有未被考虑的潜在风险。
- **触发场景**：新项目上线前推演、技术方案评审、面试准备。

### 6. `grill-with-docs` - 方案诘问与文档同步沉淀
- **核心定位**：在 `grill-me` 压力测试的基础上增加“文档沉淀”能力。
- **主要能力**：
  - 一边对你的思路和设计进行无情拷问，一边将讨论出的共识即时整理为结构化的**架构决策记录（ADR）**和**专业词汇表（Glossary）**。
- **触发场景**：团队决策、长期项目架构设计、需要产出标准文档的研讨会。

### 7. `obsidian-cli` - Obsidian 命令行控制
- **核心定位**：与本地正在运行的 Obsidian 笔记库进行系统级联动。
- **主要能力**：
  - 无需手动打开笔记，直接通过 CLI 查找、读取、创建或追加笔记。
  - 管理 Obsidian 笔记的元数据属性（Frontmatter Properties）及待办任务。
- **触发场景**：笔记自动化管理、从终端或外部工具向 Obsidian 同步数据。

### 8. `obsidian-markdown` - Obsidian 专属语法编写规范
- **核心定位**：Obsidian 用户的写作助手。
- **主要能力**：
  - 精确遵循 Obsidian 特有 Markdown 语法规则（双链 `[[文件名]]`、图片/笔记内嵌 `![[文件名]]`、高亮块 `> [!NOTE]` 等）。
  - 规范生成符合个人知识管理（PKM）标准的网状双链笔记。
- **触发场景**：整理知识库、撰写读书笔记、构建主题研究卡片。

### 9. `office-transform` - Office 与 PDF 文档安全提取
- **核心定位**：结构化处理办公文档，恪守“原文件只读”的安全底线。
- **主要能力**：
  - 从 Excel 表格、Word 文档、PowerPoint 演示稿或 PDF 中定向提取段落、表格、图表。
  - 将提取结果转换并生成全新的派生文件（如将 Excel 区域导出为标准 Markdown 表格或 CSV）。
- **触发场景**：办公自动化、合同表格提取、文档内容格式转换。

### 10. `playwright-cli` - 网页端到端测试与操作
- **核心定位**：现代前端网页自动化标准工具。
- **主要能力**：
  - 利用 Playwright 引擎对复杂动态单页应用（SPA）进行访问、截图、表单操作与流程验证。
- **触发场景**：自动化爬虫、网页功能自动化回归测试。

### 11. `ppt-master` - PPT 演示文稿全流程大师
- **核心定位**：高水准商业 PPT 制作与美化神器。
- **主要能力**：
  - 自动根据大纲生成排版优雅、结构严谨的 `.pptx` 原生幻灯片文件。
  - 支持丰富内置图表模板、图标库、母版配色方案，并支持重构现有幻灯片视觉。
- **触发场景**：商务汇报、学术答辩、课程培训幻灯片制作。

### 12. `skill-creator` - Skill 创造器
- **核心定位**：开发与迭代 Skill 的元工具（Meta-Skill）。
- **主要能力**：
  - 协助编写符合规范的 `SKILL.md`，优化元数据配置（name、description、allowed-tools）。
  - 优化触发词描述，确保智能体在最恰当的时机精准调用。
- **触发场景**：开发新的 Agent 技能、调优已有技能的响应效果。

### 13. `skills-sh-5vgid4` (`humanizer-zh`) - 中文去 AI 味与精炼润色
- **核心定位**：告别机械感与公文套话，让文字回归人味。
- **主要能力**：
  - 针对带有浓厚“AI 腔调”（如无意义的副词、重复的模板总结句、刻板的排比句）的中文稿件进行深度脱水。
  - 保留核心论据与作者真实口吻的同时，使文字更简练、有骨架、具备真实专业感。
- **触发场景**：公众号文章校对、报告精炼、文案润色。

### 14. `web-browser` - Chrome 原生自动化控制
- **核心定位**：底层 CDP（Chrome DevTools 协议）自动化方案。
- **主要能力**：
  - 支持 Headless（无头静默）或带界面的 Chrome 自动化控制，提供最底层的网络拦截、DOM 检查与性能排查能力。
- **触发场景**：高级网页抓取、网络性能分析、无头浏览器批量作业。

---

## 🛠️ 目录结构

```text
skill/
├── LICENSE
├── README.md                  # 本文档：完整的中文技能索引与说明
└── skills/                    # 所有技能集合
    ├── agent-butler/
    ├── cherry-browser/
    ├── cherry-tool-guide/
    ├── find-skills/
    ├── grill-me/
    ├── grill-with-docs/
    ├── obsidian-cli/
    ├── obsidian-markdown/
    ├── office-transform/
    ├── playwright-cli/
    ├── ppt-master/
    ├── skill-creator/
    ├── skills-sh-5vgid4/
    └── web-browser/
```

---

## 💡 如何在 Cherry Studio 中挂载或恢复这些 Skill

1. 打开 Cherry Studio 设置 -> **Agent Skills** 技能管理界面。
2. 您可以通过本仓库中对应技能的 `SKILL.md` 链接直接导入，或者将本仓库克隆至本地后直接引用对应文件夹。
3. 任何时候修改或新增技能，本仓库均作为您的云端版本中心与安全备份。
