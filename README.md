# 🐱 耄耋（maodie）— 心理洞察型人格助手 + 奇门遁甲子技能

> 一个具有人格、思考能力和洞察能力的陪伴型 AI 技能，内置奇门遁甲排盘能力。

> ⚠️ **关于"耄耋"**：耄耋（mào dié）本是八十岁老人的代称，但本技能中**纯属玩梗**，并非角色设定为老人。耄耋是一种人格象征——代表长期观察、沉淀、理解人与世界的气质。不是年龄设定，不是老人角色。

## 身份标识

- **耄耋自称：** 🐱🐱（猫猫）
- **耄耋称呼用户：** 🐭🐭（鼠鼠）
- 这不是宠物扮演，而是一种轻松、亲切的陪伴型人格标识

## 概述

耄耋作为 Hermes Agent 的心理洞察技能，核心定位是：

- 理解用户真正表达的内容
- 发现语言背后的情绪
- 探索用户隐藏的需求
- 帮助用户认识自己
- 提供多角度思考

## 技能架构

```
maodie/                      ← 耄耋主技能
├── SKILL.md                 ← 核心人格、心理分析框架、沟通风格
├── memory/                  ← 用户记忆和长期陪伴数据
├── references/              ← 心理分析参考文件
│   ├── chinese_culture.md
│   ├── conversation_style.md
│   ├── emotional_patterns.md
│   ├── psychology_frameworks.md
│   └── reasoning_framework.md
└── qimen-dunjia/            ← 奇门遁甲子技能（仅计算，不输出）
    ├── SKILL.md             ← 奇门排盘工作流
    ├── references/
    │   ├── ruleset-mainline.md
    │   ├── interview.md
    │   ├── yongshen.md
    │   ├── geju.md
    │   └── examples.md
    └── scripts/
        ├── qimen_cli.py     ← 排盘计算脚本（依赖 lunar_python）
        └── requirements.txt
```

## 调用关系

```
用户 → 耄耋（🐱🐱）
         ↓ 用户说"帮我用奇门看看"
      耄耋调用 qimen-dunjia 子技能
         ↓
      qimen 做排盘计算（scripts/qimen_cli.py）
         ↓
      qimen 返回计算结果给耄耋
         ↓
      耄耋解读结果，用自己的风格输出给用户
```

**核心原则：** qimen 只做计算，不输出。所有输出由耄耋完成。

## 奇门遁甲子技能说明

`qimen-dunjia/` 子技能来源于 [FANzR-arch/Numerologist_skills](https://github.com/FANzR-arch/Numerologist_skills/tree/main/qimen-dunjia)，在原仓库基础上做了以下适配：

- **修改为子技能模式**：原技能设计为独立响应，现改为仅由耄耋调用，只做计算不直接输出
- **输出层剥离**：原技能的第 5 步（解读与输出）和输出风格部分移交给耄耋执行
- **路径适配**：脚本路径以耄耋技能目录为基准
- **保留完整计算能力**：排盘脚本、参考文件、规则集均完整保留

奇门遁甲默认使用 `mainline-cn-v1` 规则集：
- 体系：时家转盘奇门
- 默认时区：Asia/Shanghai
- 定局：置闰法工程化实现
- 中宫/寄宫：一律寄坤处理

## 安装方式

### 方式一：Hermes Agent 技能安装

将 `maodie/` 目录复制到 Hermes Agent 的 skills 目录：

```bash
cp -r maodie ~/.hermes/skills/leisure/maodie
```

### 方式二：依赖安装

奇门排盘脚本需要 Python 依赖：

```bash
pip install "lunar_python>=1.4.8,<2" "tzdata>=2024.1"
```

## 使用

激活耄耋后，输入触发词 **"你好耄耋"** 即可开始对话。

当需要奇门排盘时，对耄耋说 **"帮我用奇门看看"**，耄耋会自动完成访谈→排盘→解读的全流程。

## 致谢

- 奇门遁甲子技能基于 [FANzR-arch/Numerologist_skills](https://github.com/FANzR-arch/Numerologist_skills) 的 `qimen-dunjia` 模块改编
- 排盘脚本使用 [lunar_python](https://pypi.org/project/lunar-python/) 库
- 耄耋人格设计参考了心理动力学、人本主义、接纳承诺疗法等心理学框架

## 许可

MIT
