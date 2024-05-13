## 各平台rime输入法
| **系统平台** | **输入法名称** | **来源链接** | **备注说明** |**配置文件位置**|
| :--: | :--: | :--: | :--: |:--: |
| **macOS** | [鼠须管Squirrel](https://github.com/LEOYoon-Tsaw/squirrel/releases) | https://github.com/LEOYoon-Tsaw/squirrel/releases | 更多适应macOS的更新 |~/Library/Rime/squirrel.yaml|
| **Windows** | [小狼毫Weasel](https://rime.im/) | https://rime.im/ | 官方更新站点 |%APPDATA%/Rime/weasel.yaml|
| **Linux** | [fcitx5-rime](https://github.com/fcitx/fcitx5-rime) [ibus-rime](https://github.com/rime/ibus-rime) | https://github.com/fcitx/fcitx5-rime <br>https://github.com/rime/ibus-rime , | 建议使用 Linux 对应包管理工具安装 |~/.config/ibus/rime/ibus_rime.yaml <br> ~/.local/share/fcitx5/rime/名称暂缺|
| **Android** | [fcitx5-Android](https://github.com/fcitx5-android/fcitx5-android)| https://github.com/fcitx5-android/fcitx5-android | 建议从 github 或者酷安市场安装 |参照软件内说明|
| **IOS** | [仓输入法Hamster](https://github.com/imfuxiao/Hamster) | https://github.com/imfuxiao/Hamster | 呃，iOS 应用商店安装 |参照软件内说明，可用wifi上传配置文件|


## 说明：
个人修改自用版(mac版)，[lufs的reimu主题](https://github.com/LufsX/rime)+[雾凇拼音的词库配置](https://github.com/iDvel/rime-ice)，另外将候选词数量调整为10个。
其他的尝试看怎么能不同更新，毕竟有人维护的才更具有生命力，另外配合[落霞文楷字体](https://github.com/lxgw/LxgwWenKai)食用更香。
如果有需要更新的，请提醒我。

## 配置页面参照：

`macOS：`[lufs'blog](https://blog.isteed.cc/post/rime-2022/)

`Windows：`[雾凇拼音配置](https://dvel.me/posts/rime-ice/)

`Linux：`[薄荷拼音配置](https://www.mintimate.cc/zh/demo/)
参照以上三个，主要是可以蹭配置方案，熟悉后再自己修改。另外Linux如果出现不能输入的情况:

添加环境变量：
- `iBus：`
 [参考来源](https://wiki.archlinuxcn.org/wiki/IBus)
        如果你在输入中文时遇到问题，检查你的 locale 设置。比如在香港，export LANG=zh_HK.utf8。
        如需 ibus 随 gnome 启动，把这些加入 ~/.profile 后重启 gnome。
    
           export GTK_IM_MODULE=ibus
           export XMODIFIERS=@im=ibus
           export QT_IM_MODULE=ibus
           ibus-daemon -d -x

- `fcitx5-rime:`
   [参考来源](https://wiki.archlinuxcn.org/wiki/Fcitx5)
        编辑 /etc/environment 并添加以下几行，然后重新登录[1]：
        
            GTK_IM_MODULE=fcitx
            QT_IM_MODULE=fcitx
            XMODIFIERS=@im=fcitx
            SDL_IM_MODULE=fcitx
            GLFW_IM_MODULE=ibus

gnome桌面环境特别说明：

- 针对gnome桌面再wayland模式下，QQ和某些情况下，输入法失效及不显示状态栏输入法状态的，fcitx5需安装[Input Method Panel](https://extensions.gnome.org/extension/261/kimpanel/)，
- 针对候选词横排或纵行调整失效的，可安装[ibus-tweaker](https://extensions.gnome.org/extension/2820/ibus-tweaker/)即可调整，以上两条，针对ibus框架下的其他输入法也有效果。

KDE桌面[Wayland](https://blog.merrkry.com/posts/2024-03-24-kde-fcitx5/)环境下随机上字符解决方式：

- 在：/etc/environment 文件中，仅增加以下字符，别的关于输入法的别加。
  ```
  XMODIFIERS=@im=fcitx
  ```

- QQ或chromium输入异常，在/usr/share/applications/qq.desktop：  Exec=后命令后增加以下字符：
```
--enable-features=UseOzonePlatform --ozone-platform=wayland --enable-wayland-ime
```

## 本配置文件配置示意
![macOS输入法配置示意](_macOS鼠须管配置示意.wbm)



# 雾凇拼音

![demo](./others/demo.webp)

功能齐全，词库体验良好，长期更新修订。

<br>

[Rime Input Method Engine / 中州韵输入法引擎](https://rime.im/) 是一个跨平台的输入法算法框架。

这里是 Rime 的一份配置仓库，用户需要下载各平台对应的前端，并将此配置应用到配置目录。

雾凇拼音提供了一套开箱即用的完整配置，包含了输入方案（全拼、双拼）、长期维护的词库及各项扩展功能。

详细介绍：[Rime 配置：雾凇拼音](https://dvel.me/posts/rime-ice/)

[常见问题](https://github.com/iDvel/rime-ice/issues/133)

[更新日志](./others/CHANGELOG.md)

<br>

## 基本套路

- 简体 | 全拼 | 双拼
- 主要功能
    -   [melt_eng](https://github.com/tumuyan/rime-melt) 英文输入（@tumuyan | [Apache 2.0](https://github.com/tumuyan/rime-melt/blob/master/LICENSE)）
    -   [优化英文输入体验](https://dvel.me/posts/make-rime-en-better/)
    -   [部件拆字方案](https://github.com/mirtlecn/rime-radical-pinyin) 反查、辅码（@mirtlecn | [CC BY-SA 4.0](https://github.com/mirtlecn/rime-radical-pinyin/blob/master/LICENSE)）
    -   自整理的 Emoji
    -   [以词定字](https://github.com/BlindingDark/rime-lua-select-character)（@BlindingDark | [LGPL 3.0](https://github.com/BlindingDark/rime-lua-select-character/blob/master/LICENSE)）
    -   [长词优先](https://github.com/tumuyan/rime-melt/blob/master/lua/melt.lua)（@tumuyan | [Apache 2.0](https://github.com/tumuyan/rime-melt/blob/master/LICENSE)）
    -   [Unicode](https://github.com/shewer/librime-lua-script/blob/main/lua/component/unicode.lua)（@shewer | [MIT](https://github.com/shewer/librime-lua-script/blob/main/lua/component/unicode.lua)）
    -   [数字、人民币大写](https://github.com/yanhuacuo/98wubi/blob/master/lua/number.lua)（@98wubi）
    -   日期、时间、星期、[农历](https://github.com/boomker/rime-fast-xhup)（@boomker | [LGPL 3.0](https://github.com/boomker/rime-fast-xhup/blob/master/LICENSE)）
    -   常见错音错字提示
    -   置顶候选项
    -   所有标点符号直接上屏，/ 模式改为 v 模式，/ 直接上屏
    -   增加了许多拼音纠错
- 简体字表、词库
    -   [《通用规范汉字表》](https://github.com/iDvel/The-Table-of-General-Standard-Chinese-Characters)
    -   [华宇野风系统词库](http://bbs.pinyin.thunisoft.com/forum.php?mod=viewthread&tid=30049)（@野风）
    -   [清华大学开源词库](https://github.com/thunlp/THUOCL)（@THUNLP | [MIT](https://github.com/thunlp/THUOCL/blob/master/LICENSE)）
    -   [现代汉语常用词表](https://gist.github.com/indiejoseph/eae09c673460aa0b56db)（@Joseph cheng）
    -   [腾讯词向量](https://ai.tencent.com/ailab/nlp/en/download.html)（@Tencent AI Lab | [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/)）
    -   参考
        -   《现代汉语词典》
        -   《同义词词林》
        -   《新华成语大词典》
- 词库修订
    - 校对大量异形词、错别字、错误注音
    - 全词库完成注音
    - 同义多音字注音

<br>

## 长期维护词库

因为没有找到一份比较好的词库，干脆自己维护一个。综合了几个不错的词库，精心调教了很多。

主要维护的词库：

- `8105` 字表。
- `base` 基础词库。
- `ext` 扩展词库，小词库。
- `tencent` 扩展词库，大词库。
- Emoji

维护内容主要是异形词、错别字的校对，错误注音的修正，缺失的常用词汇的增添，词频的调整。

欢迎在词库方面提 issue [#666](https://github.com/iDvel/rime-ice/issues/666) ，我会及时更新修正。

<br>

## 使用说明

⚠️ 单独使用词库注意事项：`rime_ice.dict.yaml` 下面包含了大写字母，这和配置有些许绑定，可以直接删除，详细说明：[#356](https://github.com/iDvel/rime-ice/issues/356)

雾凇拼音中多个文件可能与其他方案同名冲突，如果是新手想一键安装，建议备份原先配置，清空配置目录再导入。

配置目录为小狼毫的 `%APPDATA%\Rime`，鼠须管的 `~/Library/Rime`，可通过右键菜单栏图标打开。

### 手动安装

将仓库所有文件复制粘贴到配置目录，重新部署。

更新词库，手动覆盖 `cn_dicts` `en_dcits` `opencc` 三个文件夹。

### 东风破 [plum](https://github.com/rime/plum)

选择配方（`others/recipes/*.recipe.yaml`）来进行安装或更新。

词库配方只是更新具体词库文件，并不更新 `rime_ice.dict.yaml` 和 `melt_eng.dict.yaml`，因为用户可能会挂载其他词库。如果更新后部署时报错，可能是增、删、改了文件名，需要检查上面两个文件和词库的对应关系。

℞ 安装或更新全部文件

```
bash rime-install iDvel/rime-ice:others/recipes/full
```

℞ 安装或更新所有词库文件（包含下面三个）

```
bash rime-install iDvel/rime-ice:others/recipes/all_dicts
```

℞ 安装或更新拼音词库文件（ `cn_dicts/` 目录内所有文件）

```
bash rime-install iDvel/rime-ice:others/recipes/cn_dicts
```

℞ 安装或更新英文词库文件（ `en_dicts/` 目录内所有文件）

```
bash rime-install iDvel/rime-ice:others/recipes/en_dicts
```

℞ 安装或更新 opencc （ `opencc/` 目录内所有文件）

```
bash rime-install iDvel/rime-ice:others/recipes/opencc
```

下面这个配方会在 `radical_pinyin.custom.yaml` 和 `melt_eng.custom.yaml` 里将 `speller/algebra` 修改为对应的双拼拼写，选择一个自己使用的双拼作为参数。

℞ 双拼补丁

```
bash rime-install iDvel/rime-ice:others/recipes/config:schema=flypy
bash rime-install iDvel/rime-ice:others/recipes/config:schema=double_pinyin
bash rime-install iDvel/rime-ice:others/recipes/config:schema=mspy
bash rime-install iDvel/rime-ice:others/recipes/config:schema=sogou
bash rime-install iDvel/rime-ice:others/recipes/config:schema=abc
bash rime-install iDvel/rime-ice:others/recipes/config:schema=ziguang
```

### 仓输入法 [Hamster](https://github.com/imfuxiao/Hamster)

参考 [如何导入"雾淞拼音输入方案"](https://github.com/imfuxiao/Hamster/wiki/%E5%A6%82%E4%BD%95%E5%AF%BC%E5%85%A5%22%E9%9B%BE%E6%B7%9E%E6%8B%BC%E9%9F%B3%E8%BE%93%E5%85%A5%E6%96%B9%E6%A1%88%22)

仓输入法目前已内置雾凇拼音，也可以通过【输入方案设置 - 右上角加号 - 方案下载 - 覆盖并部署】来更新雾凇拼音。

使用九宫格，需要同时启用九宫格方案（输入方案设置）和九宫格布局（键盘设置 - 键盘布局 - 中文 9 键）。

### 自动部署脚本

[Mark24Code/rime-auto-deploy](https://github.com/Mark24Code/rime-auto-deploy) 一个自动部署脚本，集成了雾凇拼音，帮助无痛快速安装、部署 Rime 输入法（中州韵、小狼毫，鼠须管）以及部署配置。

### Arch Linux

使用 AUR helper 安装 [rime-ice-git](https://aur.archlinux.org/packages/rime-ice-git) 包即可。

```bash
# paru 默认会每次重新评估 pkgver，所以有新的提交时 paru 会自动更新，
# yay 默认未开启此功能，可以通过此命令开启
# yay -Y --devel --save

paru -S rime-ice-git
# yay -S rime-ice-git
```

推荐使用[补丁](https://github.com/rime/home/wiki/Configuration#補靪)的方式启用。

参考下面的配置示例，修改对应输入法框架用户目录（见下）中的 `default.custom.yaml` 文件

- iBus 为 `$HOME/.config/ibus/rime/`
- Fcitx5 为 `$HOME/.local/share/fcitx5/rime/`

<details>
<summary>default.custom.yaml</summary>

```yaml
patch:
  # 仅使用「雾凇拼音」的默认配置，配置此行即可
  __include: rime_ice_suggestion:/
  # 以下根据自己所需自行定义，仅做参考。
  # 针对对应处方的定制条目，请使用 <recipe>.custom.yaml 中配置，例如 rime_ice.custom.yaml
  __patch:
    key_binder/bindings/+:
      # 开启逗号句号翻页
      - { when: paging, accept: comma, send: Page_Up }
      - { when: has_menu, accept: period, send: Page_Down }
```

</details>

<br>

## 感谢 ❤️

感谢上述提到的词库、方案及功能参考。

感谢 [@Huandeep](https://github.com/Huandeep) 整理的多个词库。

感谢 [@Mirtle](https://github.com/mirtlecn) 完善的多个功能。

感谢所有贡献者。

搜狗转 Rime：[lewangdev/scel2txt](https://github.com/lewangdev/scel2txt)

大量参考 [校对标准论坛](http://www.jiaodui.com/bbs/)

Thanks to JetBrains for the OSS development license.

[![JetBrains](https://resources.jetbrains.com/storage/products/company/brand/logos/jb_beam.svg)](https://jb.gg/OpenSourceSupport)

<br>

## 赞助 ☕

如果觉得项目不错，可以请 Dvel 吃个煎饼馃子。

<img src="./others/sponsor.webp" alt="请 Dvel 吃个煎饼馃子" width=600 />
