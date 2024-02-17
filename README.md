## sonssBBS
为 [sonssBBS](https://0xffff.one/) 定制的 [flarum](https://github.com/flarum/flarum)。

我们正在努力：

1. 根据 sonssBBS 社区需求进行定制。
2. 基于云的现代 Flarum 开发和部署工作流程。
3. 鼓励更多人参与Flarum社区并为Flarum社区做出贡献。

## 定制
**Flarum sonssBBS** 的定制由以下部分组成：
1. 使用我们自定义的 `composer.json` / `composer.lock` 配置初始化 [Flarum Skeleton](https://github.com/flarum/flarum)（包含我们正在使用的扩展）。
2. 对 `vendor/` 中的扩展进行修补，以进行一些小的更改，而无需发布新的 Composer 包（请参阅 [patches/README.md](patches/README.md)）。
3. `extend.php` 中的自定义 [flarum 扩展程序](https://docs.flarum.org/extend/start#extenders)。
4. 自定义第三方扩展作为子模块集成到此存储库中。

我们定制的功能包括：
1. 支持全局资产CDN配置。
2. 将头像保存到 S3 兼容存储而不是本地磁盘（感谢 [askvortsov1/flarum-azure-poc](https://github.com/askvortsov1/flarum-azure-poc)）。
3. 添加对 [blomstra/flarum-redis](https://github.com/blomstra/flarum-redis) 扩展的支持（针对队列/缓存/会话），使队列工作器能够使用[后台任务](https:// /docs.flarum.org/internal/package-manager#background-tasks）异步。
4. 添加对自定义头 HTML 的支持，例如在“config.php”中添加一些“<script>”/“<link>”/“<meta>”标签。
5. 将一些硬编码的 JsDelivr 资源 URL 替换为字节跳动的 cdn（适用于中国大陆用户）。
6. `composer.json` 所需的所有扩展
7. ...

## 本地开发环境设置
我们将[开发容器](https://containers.dev/) 与 LNMP 配置一起使用，以节省配置环境所需的时间。

配置本地开发环境的步骤：
1. 在您的开发计算机上安装 Docker（Docker Desktop / Docker CE / OrbStack 等）。
2. 安装 VSCode 和 [开发容器 VSCode 扩展](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)。
3. 只需克隆这个存储库并使用 VSCode 打开它，然后 VSCode 就会通知您在开发容器中打开该存储库。
4. 开发容器初始化后，打开 `http://localhost:8080` 并查看您的 Flarum 应用程序实例（它会自动将端口转发到本地）。

或者您可以使用此存储库创建一个新的 GitHub 代码空间，然后开始开发。

## 生产部署
基本上运行 **sonssBBS** 网站需要两个 Docker 容器实例。

1. **Flarum 0x**, latest pre-built image: `ghcr.io/0xffff-one/flarum-0x:latest`.
2. **兼容 MySQL 的 DBMS**、MySQL、MariaDB 或其他，使用支持 [ngram](https://dev.mysql.com/doc/refman/5.7/en/fulltext-search-ngram.html) 的 MySQL用于 CJK 全文搜索。

您可以通过 [Docker Compose](./docker-compose.yml) 部署它们。

## Contributors
This project exists thanks to all the people who contribute.

<a href="https://github.com/0xffff-one/flarum-0x/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=0xffff-one/flarum-0x" />
</a>

## Reference
 * [Flarum Community](https://discuss.flarum.org/)
 * [Flarum Documentation](https://docs.flarum.org/)
 * [Extending Flarum | Flarum Documentation](https://docs.flarum.org/extend/)
 * [Flarum 中文社区](https://discuss.flarum.org.cn/)
 * [ECNU-Forum/ECNU-Forum](https://github.com/ECNU-Forum/ECNU-Forum)

## License

Flarum is open-source software licensed under the [MIT License](https://github.com/flarum/flarum/blob/master/LICENSE).

