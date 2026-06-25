# Contributing

本项目按队内协作开发流程维护：`main` 是稳定主线，所有功能都通过分支和 Pull Request 合并，由项目负责人审核。

## Branches

- `main`：稳定主线，只接受通过审核的 PR 合并。
- `feature/<short-name>`：新功能分支。
- `fix/<short-name>`：缺陷修复分支。
- `docs/<short-name>`：文档调整分支。
- `chore/<short-name>`：构建、脚本、依赖和仓库维护分支。

示例：

```bash
git checkout main
git pull
git checkout -b feature/training-records
```

## Pull Requests

- PR 目标分支固定为 `main`。
- PR 标题和描述使用中文。
- PR 描述需要说明做了什么、怎么验证、是否影响部署或配置。
- 不要把 `deploy/.env`、日志、构建产物、IDE 配置提交到仓库。
- 不要在 PR 中引入本地密码登录、自签 JWT、demo token 或拆分 `student_identity` 的实现。

## Review

- 所有 PR 必须经过负责人审核后合并。
- 推荐使用 squash merge，让 `main` 历史保持清晰。
- 不要 force push `main`，不要直接删除 `main`。

## Verification

Java 代码变更提交 PR 前执行：

```bash
mvn clean verify
```

`mvn clean verify` 会运行单元测试和 JaCoCo 覆盖率检查。当前代码模块的 JaCoCo 行覆盖率门槛是 `70%`。

部署配置变更提交 PR 前执行对应配置检查，例如：

```bash
docker compose --env-file deploy/.env.example -f deploy/docker-compose.yml config
```

文档-only 变更不要求 Maven 校验。
