# 秋秋信息图制作器

把学习主题、文章、知识资料或商业议题整理成结构清晰、可直接用于图片生成模型的中文信息图提示词，也可以在支持图片生成的 Codex 环境中直接跑图。

## 当前模板

| 模板 | 适用场景 | 主要结构 |
| --- | --- | --- |
| 康奈尔笔记 | 学习、复习、教材总结页 | 线索栏、笔记栏、总结栏、一句话记忆 |
| 高级咨询风 | 商业分析、方法论、战略流程、矩阵图 | 三层标题、单一商业隐喻、3–6 个模块、结论区 |

技能会根据语境自动选择模板：学习复习场景默认使用康奈尔笔记；汇报、决策、商业或研究分析场景默认使用高级咨询风。

## 使用示例

生成康奈尔笔记提示词：

```text
使用 $qiuqiu-infographic-maker，把“费曼学习法”整理成一张康奈尔笔记信息图提示词。
```

生成高级咨询风信息图：

```text
使用 $qiuqiu-infographic-maker，把这篇文章制作成麦肯锡风信息图：[粘贴文章]
```

直接生成图片：

```text
使用 $qiuqiu-infographic-maker，把“个人知识管理系统”制作成高级咨询风信息图，直接跑图。
```

## 工作方式

1. 明确信息图目标、受众与单页范围。
2. 提炼核心模块和知识关系。
3. 选择流程、因果、层级、比较或系统结构。
4. 套用对应模板并填入具体内容。
5. 检查事实、中文可读性、信息密度和视觉层级。
6. 按用户要求输出提示词或直接生成图片。

## 文件结构

```text
qiuqiu-infographic-maker/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── cornell-notes.md
    ├── consulting-infographic.md
    ├── qiuqiu-infographic-method.md
    └── standards.md
```

- `SKILL.md`：触发规则、模板路由和统一工作流。
- `cornell-notes.md`：康奈尔笔记规划规则与提示词模板。
- `consulting-infographic.md`：高级咨询风结构选择与提示词模板。
- `qiuqiu-infographic-method.md`：从主题到视觉结构的通用方法。
- `standards.md`：内容、版面、中文文字和跑图标准。

生成图片默认保存在本地 `outputs/`，该目录已被 Git 忽略，不会提交到仓库。

## 扩展模板

新增信息图类型时：

1. 在 `references/` 新建独立模板文件。
2. 在 `SKILL.md` 的模板路由表中添加触发词和入口。
3. 复用统一的事实检查、信息密度和输出约定。
4. 运行技能校验：

   ```bash
   python3 tools/validate_skill.py .
   ```
