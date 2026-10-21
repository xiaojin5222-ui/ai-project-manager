# AI 项目管家

一个面向 Codex 编码任务的中文技能：先把需求、范围、方案和验收说清楚，再在已批准范围内自主实现，用实际检查证据交付结果。

版本：`0.1.0` 预览版，采用 [MIT 许可证](LICENSE)。

[GitHub 仓库](https://github.com/xiaojin5222-ui/ai-project-manager) · [v0.1.0 发布页](https://github.com/xiaojin5222-ui/ai-project-manager/releases/tag/v0.1.0) · [下载 ZIP](https://github.com/xiaojin5222-ui/ai-project-manager/releases/download/v0.1.0/ai-project-manager-v0.1.0.zip)

## 适用场景

- 新项目、重要功能、跨模块变更：先形成可批准的完整计划，确认后持续推进。
- 目标明确、局部且可逆的低风险修改：简述改动与检查方法，直接完成已授权工作。
- 已有具体计划和验收批准：沿用现有批准，避免重复确认。

一般问答和单纯文案写作不需要这个技能。技能提供工作方法，不提供独立项目管理软件，也不授予部署、发布或其他外部操作权限。

## 安装

需要能够加载本地技能的 Codex 环境。只安装 `ai-project-manager/` 子目录；外层文档和示例供人阅读。

1. 从 [v0.1.0 发布页](https://github.com/xiaojin5222-ui/ai-project-manager/releases/tag/v0.1.0) 下载 `ai-project-manager-v0.1.0.zip` 和同页附件 `SHA256SUMS`，按下文校验后解压。
2. 选择安装范围，将整个 `ai-project-manager/` 文件夹复制到以下一个目录：
   - 当前用户使用：`~/.agents/skills/ai-project-manager/`。
   - 仅当前项目使用：项目根目录的 `.agents/skills/ai-project-manager/`。
3. 确认目标中的文件结构如下，然后重新打开需要使用技能的会话。

```text
ai-project-manager/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── templates.md
```

如目标位置已有同名技能，先检查和备份现有内容，再替换；不要把新文件夹再次嵌套进旧的同名目录。

在 macOS 或 Linux 上，可在解压后的仓库根目录运行以下命令，安装到当前用户的技能目录：

```sh
mkdir -p "$HOME/.agents/skills"
if [ -e "$HOME/.agents/skills/ai-project-manager" ] || [ -L "$HOME/.agents/skills/ai-project-manager" ]; then
  echo "目标已存在，请先检查、备份并移走现有技能，再重试。"
else
  cp -R ai-project-manager "$HOME/.agents/skills/ai-project-manager"
fi
```

安装位置依据 [OpenAI 官方技能指南](https://learn.chatgpt.com/docs/build-skills)。已在 macOS 的内置 Codex CLI `0.163.0-alpha.10.2` 验证用户级原生发现和显式技能调用；桌面选择器 UI 与其他平台尚未验证。具体范围见 [LIMITATIONS.md](LIMITATIONS.md)。

## 校验下载内容

发布页的 `SHA256SUMS` 记录 ZIP 压缩包的 SHA-256 摘要。在 ZIP 和这个附件所在目录运行：

```sh
shasum -a 256 -c SHA256SUMS
```

解压后，进入包含 `README.md` 的目录，再运行相同命令。此时使用的是包内的另一份 `SHA256SUMS`，用于校验包内各文件；清单不包含自身。Linux 上也可使用 `sha256sum -c SHA256SUMS`。

检查输出中的文件均应显示 `OK`；如果文件缺失或摘要不符，先重新下载并核对版本，再安装。校验用于确认内容一致，不代表技能行为或业务流程已经通过验证。公开下载和下载后安装的验证结果以对应版本的发布说明为准。

## 使用

在 Codex CLI 或 IDE 中，可通过 `/skills` 查找技能，或在请求中显式写出 `$ai-project-manager`：

```text
使用 $ai-project-manager，为当前项目增加待办清单。
先查看已有实现，明确本次范围、实施方案和可观察的验收标准，
给我完整计划；我确认后再实现。
```

对于明确的局部修改：

```text
使用 $ai-project-manager，把当前页面的“提交”按钮文字改成“保存”。
这是已授权的局部文案修改，请按轻量流程完成并核对显示结果。
```

在支持技能选择的 ChatGPT 桌面端，可用 `@` 选择“AI 项目管家”。如果技能未出现，先核对安装范围、目录层级和当前客户端是否支持本地技能。

完整流程会把任务整理为需求与计划、可观察验收标准、业务里程碑和交付记录。已有相同范围、方案与验收的明确批准时可继续执行。实质范围或风险变化时，只暂停受影响步骤并说明待决定事项。

交付记录区分“已编写”“已测试”“已现场验证”“已交付”，未运行的检查明确标为未验证。示例见 [虚构待办清单任务](examples/task-list.md)，使用边界见 [LIMITATIONS.md](LIMITATIONS.md)。

## 包内内容

- `ai-project-manager/`：可安装的技能运行文件。
- `examples/task-list.md`：完全虚构的使用示例，不是测试结果。
- `CHANGELOG.md`：版本记录。
- `LIMITATIONS.md`：能力和验证范围。
- `LICENSE`：MIT 许可证全文。
- `SHA256SUMS`：包内文件的 SHA-256 清单。

无需专用脚本或额外服务。实际开发所需的语言、依赖、测试工具和外部系统权限由目标项目决定。

## 分享

介绍技能时可分享 [仓库链接](https://github.com/xiaojin5222-ui/ai-project-manager)；需要固定版本时分享 [v0.1.0 发布页](https://github.com/xiaojin5222-ui/ai-project-manager/releases/tag/v0.1.0)。转发 ZIP 时同时提供发布附件 `SHA256SUMS`，并保留包内的 `LICENSE`。

## 卸载

从安装位置移走 `ai-project-manager/` 文件夹，再重新打开会话。卸载技能不会回退它此前在项目中完成的修改。
