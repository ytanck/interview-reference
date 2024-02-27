Contributing 贡献
====

感谢您对**备忘清单**贡献的兴趣👍👍，是像您这样的人使 [`Quick Reference`](https://ytanck.github.io/interview-reference) 成为如此出色的网站 🎉🎉。随时提交问题和增强请求。

`docs/{filename}.md` 文件将被处理成备忘清单，让我们创建或编辑一个 `markdown` 文件：

## 前沿问题

```markdown
备忘清单 标题
===

这是您可以在 Quick Reference 备忘清单上使用的样式参考！【备忘清单介绍】
```

只需要 `标题<h1>` 和 `介绍` (标题下面)。脚本会自动识别，通过 GitHub Actions 自动发布 [`Quick Reference`](https://ytanck.github.io/interview-reference) 网站。

## 目录结构

```bash
.
├── CONTRIBUTING.md   # 贡献说明
├── Dockerfile
├── LICENSE
├── README.md         # Home(首页) 内容
├── dist              # 编译后的静态资源目录
├── docs              # Markdown 文档（快速参考备忘清单【速查表】）
│   ├── bash.md
│   ├── ....
│   └── yaml.md
├── package.json
└── scripts           # MD 转 HTML 的编译脚本
    ├── assets        # 存放首页 svg 图标文件资源，与 `dosc` 文件名对应
    ├── ....
    └── watch.mjs
```

## CSS 类注释

[`Quick Reference`](https://ytanck.github.io/interview-reference) 使用 [`@wcj/markdown-to-html`](https://github.com/jaywcjlove/markdown-to-html) 转换 `Markdown`，并使用 [`rehype-attr`](https://github.com/jaywcjlove/rehype-attr) 插件让其支持通过其注释语法添加类和样式。此外，您可以在 Quick Reference 备忘清单上使用样式参考：<https://ytanck.github.io/interview-reference/docs/quickreference.html>

最后，参考现有备忘清单的源代码是一个好习惯！

## 首页导航

[`Quick Reference`](https://ytanck.github.io/interview-reference) 的首页存放在仓库的根目录 `README.md`，[`Quick Reference`](https://ytanck.github.io/interview-reference) 是通过这个 `README.md` 自动生成首页导航，下面是导航实例：

```markdown
## Linux 命令

[Cron](./docs/cron.md)<!--rehype:style=background: rgb(239 68 68/var(\-\-bg\-opacity));-->
[Git](./docs/git.md)<!--rehype:style=background: rgb(215 89 62/var(\-\-bg\-opacity));-->
<!--rehype:class=home-card-->
```

首页导航图标存放在 `scripts/assets` 目录中，如果你的备忘清单定义为 `docs/cron.md`，那么你的图标就定义为 `cron.svg` 存放到 `scripts/assets` 目录中，重新编译首页当行菜单就拥有了图标。

- 图标存放在 [`scripts/assets`](https://github.com/ytanck/interview-reference/blob/main/scripts/assets) 目录中
- 图片名称与清单名称保持一致 `cron.md` -> `cron.svg` (注意大小写)
- SVG 图标尺寸 `<svg height="1em" width="1em"`
- SVG 图标颜色使用继承颜色值 `<svg fill="currentColor"`

图标可以在 [icongo 图标搜索](https://icongo.github.io/) 中搜索

### 提示配置

```markdown
[Django](./docs/django.md)<!--rehype:style=background: rgb(12 75 51/var(\-\-bg\-opacity));&class=contributing-->
```

添加 `contributing` 类名，会在卡片下方添加 _`👆待完善需要您的参与`_，添加 `data-info=👆看看还缺点儿什么？`，更换默认提示文本。

```markdown
[Django](./docs/django.md)<!--rehype:style=background: rgb(12 75 51/var(\-\-bg\-opacity));&class=tag&data-lang=Python-->
```

添加 `class=tag&data-lang=Python` 类名和参数，会在卡片右上角标记 _`Python`_

## 本地开发

```bash
$ git clone https://github.com/ytanck/interview-reference.git 
$ npm i          # 安装依赖
$ npm run build  # 编译输出 HTML
$ npm run start  # 监听 md 文件编译输出 HTML
```

或者你也可以使用 `pnpm` 或者 `yarn` 做为包管理器

## 快捷部署方法

由于中国国内访问，时常打不开，推荐您部署的镜像网站，大家可以在这里留言推荐您的镜像网站网址，我将放置在首页推荐

### 方法一，只需要克隆 gh-pages 分支代码到你的静态服务就可以了

```shell
$ git clone https://github.com/ytanck/interview-reference.git -b gh-pages
```

### 方法二，使用 [docker](https://hub.docker.com/r/wcjiang/reference) 快捷部署 web 版

```shell
$ docker pull wcjiang/reference

$ docker run --name reference --rm -d -p 9667:3000 wcjiang/reference:latest
# Or
$ docker run --name reference -itd -p 9667:3000 wcjiang/reference:latest
```

### 方法三，克隆仓库自己编译，添加导航菜单

```bash
$ git clone https://github.com/ytanck/interview-reference.git 
$ npm install    # 安装依赖
$ npm run build  # 编译输出静态页面
$ npm run start  # 开发模式，监听实时编译输出静态页面
```

文件被输出到 `dist` 目录，将 `dist` 目录静态页面部署到静态服务就可以了

<img width="423" alt="image" src="https://user-images.githubusercontent.com/1680273/203210099-cd9e1377-bceb-40cc-98f1-4c4c549a3986.png">

提供自定义菜单，在项目的根目录建立 `.env` 文件，添加下面内容

```ini
REF_URL=http://ref.xxx.cn/
REF_LABEL=网站首页
```

### 国内镜像

由于中国国内访问，时常打不开，你可以访问下面镜像网站。

- [quickref.cn](https://quickref.cn)
- [ecdata.cn](http://ref.ecdata.cn)
- [aibk.cn](https://quickref.aibk.cn)
- [jgeek.cn](http://reference.jgeek.cn/)
- [laoleng.vip](http://bbs.laoleng.vip/reference/)
- [liujiapeng.com](https://www.liujiapeng.com/)
- [dbyun.net](https://www.dbyun.net/reference/index.html)
- [dc6.fun](https://dc6.fun/reference/)
- [if010.com](https://quickref.if010.com/)
- [pipecraft.net](https://quickref.pipecraft.net/)
- [isteed.cc](https://ref.isteed.cc/)
- [1han.wiki](https://code.1han.wiki/)
- [linzhe.top](https://linzhe.top/)
- [xushanxiang.com](https://xushanxiang.com/ref/)
- [winnerzr01.github.io](https://winnerzr01.github.io/Quick-Reference/index.html)
- [quickref.hestudio.net](https://quickref.hestudio.net)
- [surcode.cn](https://ref.surcode.cn)
- [cms.im](https://quickref.cms.im/)
- [nuomiphp.com](https://reference.tool.nuomiphp.com/)
- [eryajf.net](https://ref.eryajf.net/)
- [kjchmc.cn](https://ref.kjchmc.cn/)
- [likeadmin.cn](https://www.likeadmin.cn/quickref/)
- [qiubit.cc](http://ref.qiubit.cc)
- [aoh.cc](https://aoh.cc/)
- [reference.code05.com](https://reference.code05.com/)
- [kyoma.top](https://reference.kyoma.top/)
- [quickreference.pages.dev](https://quickreference.pages.dev/)
- [code05.com](https://reference.code05.com/)
- [xhfun.cn](https://ref.xhfun.cn/)

感谢🙏

## 利用 Github Actions 定时任务来完成自动更新

在仓库添加 `.github/workflows/update-ref.yml` 文件 Github Actions 配置，感谢 @eryajf https://github.com/jaywcjlove/reference/issues/102#issuecomment-1368158419 提供方法

```yml
name: 每8个小时更新一次reference
on:
  schedule:
    - cron: '21 */8 * * *' # 定时任务
  workflow_dispatch:       # 手动运行

env: # 设置环境变量
  TZ: Asia/Shanghai # 时区（设置时区可使页面中的`最近更新时间`使用时区时间）

jobs:
  build: # 自定义名称
    runs-on: ubuntu-latest
    steps:
      - name: 🚜 拉取最新代码
        uses: actions/checkout@v3
        with:
          ref: 'main'
          repository: 'jaywcjlove/reference'

      - name: ♻️ 编译静态文件
        run: |
          echo -e 'REF_URL=https://refs.xxx.net/\nREF_LABEL=网站首页' > .env
          npm install
          npm run build

      - name: 🚁 部署到服务器
        uses: wlixcc/SFTP-Deploy-Action@v1.0
        with:
          username: 'root'   #ssh user name
          port: '22' # 远程服务器ssh端口，默认22
          server: 'prod.refs.xxx.net' # 远程服务器IP
          ssh_private_key: ${{ secrets.SSH_PRIVATE_KEY }} # 认证服务器秘钥对的私钥
          local_path: './dist/*'  # 对应我们项目打包后的静态文件路径
          remote_path: '/data/www/refs.xxx.net' # 服务器上的路径
          delete_remote_files: true
```

## 贡献

请参阅[贡献指南](./CONTRIBUTING.md)了解如何开始。一如既往，感谢我们出色的贡献者！

<!--GAMFC-->
<a href="https://github.com/jaywcjlove" title="小弟调调">
  <img src="https://avatars.githubusercontent.com/u/1680273?v=4" width="42;" alt="小弟调调"/>
</a>
<a href="https://github.com/ytanck" title="ytanck">
  <img src="https://avatars.githubusercontent.com/u/82551626?v=4" width="42;" alt="ytanck"/>
</a>
<!--GAMFC-END-->

上图贡献者列表，由 [contributors](https://github.com/ytanck/interview-reference) 自动生成贡献者图片。

## License

MIT © [ytanck](https://github.com/ytanck)
