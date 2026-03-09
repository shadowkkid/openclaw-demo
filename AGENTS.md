# AGENTS.md

## 项目概述

本项目采用前后端分离架构，后端使用 Python，前端使用 TypeScript。

## 技术栈与环境

- **Python**: 3.11+，包管理使用 `uv`
- **Node.js**: 18+，包管理使用 `npm` 或 `pnpm`
- **后端目录**: `backend/`
- **前端目录**: `frontend/`

## 开发命令

### 依赖安装

```bash
# 后端
cd backend && uv sync

# 前端
cd frontend && npm install
```

### 启动项目

```bash
# 后端
cd backend && uv run python src/main.py

# 前端
cd frontend && npm run dev
```

## 编码规范

### Python（后端）

- 使用类型注解（type hints）
- 遵循 PEP 8 风格规范
- 使用 `uv` 管理依赖，添加新依赖时使用 `uv add <package>`
- 不要手动编辑 `uv.lock`

### TypeScript（前端）

- 严格模式，不使用 `any` 类型
- 优先使用函数式组件和 hooks
- 使用 `npm` 或 `pnpm` 管理依赖

### 通用

- 文件命名使用 snake_case（Python）和 kebab-case（TypeScript）
- 每个模块/组件应职责单一
- 提交前确保代码可正常运行，无明显报错

## Git 工作流

### 分支策略

- 主分支为 `master`
- 每个功能/任务创建独立的功能分支，分支名格式：`feat/<简短描述>`，例如 `feat/user-login`
- 修复类任务分支名格式：`fix/<简短描述>`，例如 `fix/api-error-handling`

### 提交规范

- Commit message 使用 Conventional Commits 格式：
  - `feat: 添加用户登录接口`
  - `fix: 修复分页查询越界问题`
  - `refactor: 重构数据库连接池`
  - `docs: 更新 API 文档`
  - `chore: 升级依赖版本`
- 每个 commit 应当是一个原子性的变更，不要把不相关的修改混在一起

### Pull Request 要求

每完成一个功能后，必须创建 Pull Request 合并到 `master` 分支。PR 描述需包含以下内容：

#### PR 标题

用英文简洁描述本次功能，例如：`feat: new feature`

#### PR 正文模板

```markdown
## 需求描述

简要说明收到的需求是什么，要解决什么问题。

## 实现方案

概述本次采用的技术方案和关键设计决策。

## 修改文件说明

| 文件路径 | 修改类型 | 说明 |
|---------|---------|------|
| `backend/src/xxx.py` | 新增 | 说明这个文件的作用 |
| `backend/src/yyy.py` | 修改 | 说明修改了什么，为什么修改 |
| `frontend/src/xxx.tsx` | 新增 | 说明这个文件的作用 |

## 测试情况

说明如何验证本次修改的正确性。
```

#### PR 注意事项

- 每个 PR 只对应一个功能或任务，不要把多个不相关的功能放在同一个 PR
- PR 描述中的「修改文件说明」必须覆盖所有变更文件，每个文件都要写清修改目的和内容
- 创建 PR 前确保代码可正常构建和运行
- PR 分支应基于最新的 `master` 分支创建

## 禁止事项

- 不要直接在 `master` 分支上提交代码
- 不要提交 `.env`、密钥、凭证等敏感信息
- 不要提交 `node_modules/`、`__pycache__/`、`.venv/` 等生成目录
- 不要在没有理解需求的情况下开始编码，有疑问先确认
