<!---
    @title         OpenResty® Linux 包
--->

对于下列 Linux 发行版的种类和版本号，OpenResty<sup>&reg;</sup> 提供官方的预编译包。

* Ubuntu

```
    版本            版本名         支持的体系结构
    14.04           Trusty          amd64
    16.04           Xenial          amd64
    18.04           Bionic          amd64
    18.10           Cosmic          amd64
    19.04           Disco           amd64
    19.10           Eoan            amd64
```

* Debian

```
    版本           版本名        支持的体系结构
    8.x             Jessie          amd64
    9.x             Stretch         amd64
    10.x            Buster          amd64
```

* CentOS

```
    版本号         支持的体系结构
    6.x             x86_64
    7.x             x86_64, aarch64 (arm64)
    8.x             x86_64
```

* Red Hat 企业版 Linux (RHEL)

```
    版本号          支持的体系结构
    6.x             x86_64
    7.x             x86_64
    8.x             x86_64
```

* Fedora

```
    版本号          支持的体系结构
    28              x86_64
    29              x86_64
    30              x86_64
    31              x86_64
```

* Amazon Linux

```
    版本号         支持的体系结构
    1 (2018.03)    x86_64
    2              x86_64
```

* OpenSUSE Leap

```
    版本号          支持的体系结构
    15.1            x86_64
```


我们仓库的所有元数据（以及 rpm 二进制包）都是用下面的 GPG 密钥， `0xD5EDEB74` 签名的：

https://openresty.org/package/pubkey.gpg

# Ubuntu

你可以在你的 Ubuntu 系统中添加我们的 APT 仓库，这样就可以便于未来安装或更新我们的软件包（通过 `apt-get update` 命令）。
运行下面的命令就可以添加仓库（每个系统只需要运行一次）：

```bash
# 安装导入 GPG 公钥时所需的几个依赖包（整个安装过程完成后可以随时删除它们）：
sudo apt-get -y install --no-install-recommends wget gnupg ca-certificates

# 导入我们的 GPG 密钥：
wget -O - https://openresty.org/package/pubkey.gpg | sudo apt-key add -

# 安装 add-apt-repository 命令
# （之后你可以删除这个包以及对应的关联包）
sudo apt-get -y install --no-install-recommends software-properties-common

# 添加我们官方 official APT 仓库：
sudo add-apt-repository -y "deb http://openresty.org/package/ubuntu $(lsb_release -sc) main"

# 更新 APT 索引：
sudo apt-get update
```

然后就可以像下面这样安装软件包，比如 `openresty`：

```bash
sudo apt-get -y install openresty
```

这个包同时也推荐安装 `openresty-opm` 和 `openresty-restydoc` 包，所以后面两个包会缺省安装上。
如果你不想自动关联安装，可以用下面方法关闭自动关联安装：

```bash
sudo apt-get -y install --no-install-recommends openresty
```

参阅 [OpenResty Deb 包](deb-packages.html) 页面获取这个仓库里头更多可用包的信息。

# Debian

你可以在你的 Debian 系统中添加 `openresty` 仓库，这样就可以便于未来安装或更新我们的软件包（通过 `apt-get update` 命令）。
运行下面的命令就可以添加我们的仓库（每个系统只需要运行一次）：

```bash
# 安装导入 GPG 公钥时所需的几个依赖包（整个安装过程完成后可以随时删除它们）：
sudo apt-get -y install --no-install-recommends wget gnupg ca-certificates

# 导入我们的 GPG 密钥：
wget -O - https://openresty.org/package/pubkey.gpg | sudo apt-key add -

# 安装 add-apt-repository 命令
# （之后你可以删除这个包以及对应的关联包）
sudo apt-get -y install --no-install-recommends software-properties-common

# 添加我们官方 official APT 仓库：
sudo add-apt-repository -y "deb http://openresty.org/package/debian $(lsb_release -sc) openresty"

# 更新 APT 索引：
sudo apt-get update
```

然后就可以像下面这样安装软件包，比如 `openresty`：

```bash
sudo apt-get -y install openresty
```

这个包同时也推荐安装 `openresty-opm` 和 `openresty-restydoc` 包，所以后面两个包会缺省安装上。
如果你不想自动关联安装，可以用下面方法关闭自动关联安装：

```bash
sudo apt-get -y install --no-install-recommends openresty
```

参阅 [OpenResty Deb 包](deb-packages.html) 页面获取这个仓库里头更多可用包的信息。

# CentOS

你可以在你的 CentOS 系统中添加 `openresty` 仓库，这样就可以便于未来安装或更新我们的软件包（通过 `yum check-update` 命令）。运行下面的命令就可以添加我们的仓库：

```bash
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://openresty.org/package/centos/openresty.repo
```

然后就可以像下面这样安装软件包，比如 `openresty`：

```bash
sudo yum install -y openresty
```

如果你想安装命令行工具 `resty`，那么可以像下面这样安装 `openresty-resty` 包：

```bash
sudo yum install -y openresty-resty
```

命令行工具 `opm` 在 `openresty-opm` 包里，而 `restydoc` 工具在
`openresty-doc` 包里头。

列出所有 `openresty` 仓库里头的软件包：

```bash
sudo yum --disablerepo="*" --enablerepo="openresty" list available
```

参考 [OpenResty RPM 包](rpm-packages.html)页面获取这些包更多的细节。

# RHEL

你可以在你的 RHEL 系统中添加 `openresty` 仓库，这样就可以便于未来安装或更新我们的软件包（通过 `yum check-update` 命令）。添加仓库，运行下面的命令：

```bash
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://openresty.org/package/rhel/openresty.repo
```

在想 RHEL 6.x 这样的老系统上，最后那条命令可能因为 `yum-config-manager` 命令的内部问题，生成下面的错误：

```
[Errno 14] Peer cert cannot be verified or peer cert invalid
```

如果出现上述问题，你可以用下面的命令添加仓库：


```bash
sudo yum-config-manager --add-repo http://openresty.org/package/rhel/openresty.repo
```

添加了包仓库之后就可以像下面这样安装软件包，比如 `openresty`：

```bash
sudo yum install -y openresty
```

如果你想安装命令行工具 `resty`，那么可以像下面这样安装 `openresty-resty` 包：

```bash
sudo yum install -y openresty-resty
```

命令行工具 `opm` 在 `openresty-opm` 包里，而 `restydoc` 工具在
`openresty-doc` 包里头。

列出所有 `openresty` 仓库里头的软件包：

```bash
sudo yum --disablerepo="*" --enablerepo="openresty" list available
```

我们的包仓库中有某些包，比如 `perl-Test-Nginx` 和 `perl-Lemplate`，依赖开启一些可选的 RHEL 标准包仓库。比如
在 RHEL 6 和 RHEL 7 上，需要启用 RHEL 官方的 Optional RPM 包仓库。在 RHEL 7 上可以运行这条命令：

```bash
sudo subscription-manager repos --enable rhel-7-server-optional-rpms
```

在 RHEL 6 上则是这样的：

```bash
sudo subscription-manager repos --enable rhel-6-server-optional-rpms
```

而在 RHEL 8 上则需要开启 RHEL 官方的 CodeReady 仓库：

```bash
sudo subscription-manager repos --enable codeready-builder-for-rhel-8-x86_64-rpms
```

在 [OpenResty RPM 包](rpm-packages.html) 页面能看到这些包更多的细节。

请注意在 RHEL 8 上面缺少 `perl-Lemplate` 这个 RPM 包，这是因为 RHEL 8 相比 RHEL 7 从其标准仓库中移除了 `perl-Template-Toolkit`
这样的 Perl 模块包。

# Fedora

在 Fedora 系统中你可以这样来启用 `openresty` 仓库:

```bash
sudo dnf install -y dnf-plugins-core
sudo dnf config-manager --add-repo https://openresty.org/package/fedora/openresty.repo
```

然后你就可以方便的从 `openresty-openresty` 仓库中安装和更新包(通过 `dnf update` 命令)。 比如我们可以运行下面的命令来安装 `openresty`:

```bash
sudo dnf install -y openresty
```

如果想安装 `resty` 命令行工具，则像下面这样安装 `openresty-resty` 软件包：

```bash
sudo dnf install -y openresty-resty
```

命令行工具 `opm` 在 `openresty-opm` 包里，而 `restydoc` 工具在
`openresty-doc` 包里头。

列出在 `openresty-openresty` 仓库中所有可用的包, 可以这样

```bash
sudo dnf repo-pkgs openresty-openresty list available
```

在 [OpenResty RPM 包](rpm-packages.html) 页面能看到这些包更多的细节。

# Amazon Linux

你可以在你的 Amazon Linux （亚马逊 Linux）系统里用下面命令添加 `openresty` 仓库：

```bash
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://openresty.org/package/amazon/openresty.repo
```

然后你就可以像下面这样安装包了，比如说安装 `openresty`：

```bash
sudo yum install -y openresty
```

如果想安装 `resty` 命令行工具，则像下面这样安装 `openresty-resty` 软件包：

```bash
sudo yum install -y openresty-resty
```

命令行工具 `opm` 在 `openresty-opm` 包里，而 `restydoc` 工具在
`openresty-doc` 包里头。

列出在 `openresty-openresty` 仓库中所有可用的包, 可以这样

```bash
sudo yum repo-pkgs openresty-openresty list available
```

在 [OpenResty RPM 包](rpm-packages.html) 页面能看到这些包更多的细节。

请注意在 Amazon Linux 2 系统上缺少那些 `*-asan` RPM 包，因为 Amazon Linux 2 官方的 clang 包里缺少 `libclang_rt.a` 这个库文件）。

# OpenSUSE Leap

你可以在你的 OpenSUSE Leap 系统中如下所示启用 openresty 包仓库：

```bash
sudo zypper ar -g --refresh --check https://openresty.org/package/opensuse/openresty.repo
```

然后你就可以像下面这样安装包了，比如说安装 `openresty`：

```bash
sudo zypper install -y openresty
```

如果想安装 `resty` 命令行工具，则像下面这样安装 `openresty-resty` 软件包：

```bash
sudo zypper install -y openresty-resty
```

命令行工具 `opm` 在 `openresty-opm` 包里，而 `restydoc` 工具在
`openresty-doc` 包里头。

列出在 `openresty-openresty` 仓库中所有可用的包, 可以这样

```bash
sudo zypper pa -r openresty
```

请注意我们的 OpenSUSE Leap 仓库目前并没有提供独立的 `*-debuginfo` 包。我们直接在二进制程序文件中包含了
DWARF 调试符号。

在 [OpenResty RPM 包](rpm-packages.html) 页面能看到这些包更多的细节。

# 更多 Linux 发行版的支持

我们欢迎社区贡献更多的 Linux 发行版，比如 SLES, Arch, Slackware 和 Oracle Linux 的包仓库。请确保新的安装包尽可能地接近我们现有的 [RPM 安装包](rpm-packages.html)。非常感谢！

# 非 Linux 系统的安装包

目前 OpenResty 也提供针对 Windows 系统的二进制安装包，可以从[下载页面](download.html)获取。
