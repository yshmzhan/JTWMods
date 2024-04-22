# 神州志·西游 创意工坊开发手册
## 通过Harmony制作Mod
```
https://steamcommunity.com/sharedfiles/filedetails/?id=3227400181
```
## 功能介绍
目前提供有限支持，允许玩家制作并上传自己的mod来替换游戏卡牌的图片。

## mod样例测试
1. 从这里下载我们的样例[test_mod](test_mod.zip)
2. 解压得到 一个文件包：`test_mod`
3. 将`test_mod`放到游戏数据目录（需要手动创建`Mods`文件夹），如下：

   windows:
   ```
   %userprofile%\AppData\LocalLow\Z Studio\JTW\Mods\test_mod
   ```
   macOS:
   ```
   ~/Library/Application Support/Z Studio/JTW/Mods/test_mod
   ```
   
4. 启动`神州志西游`游戏
5. 会发现 `千钧之重` 和 `万里之长` 两张卡牌的图片已经被替换了。

## 自定义mod
可以基于我们提供的样例进行修改，或者重新创建一个新的mod.
### mod 结构
```
your_mod
    ├── Data
    │   ├── Assets
    │   │   └── Images                // 图片资源目录
    │   │       ├── card.jpg          // 图片资源
    │   │       └── card_2.png
    │   └── Cards
    │       └── cards_mod.csv         // 卡牌配置文件
    └── mod.json                      // mod 描述文件，无需改动。
```
### 添加图片资源
将所需的图片资源放到 `your_mod/Data/Assets/Images` 目录下。目前支持`png`, `jpeg`格式。
### 修改卡牌图片
卡牌配置文件是一个`csv`文件，需要以如下格式填写。

| Name | Key | Value |
| ------------- | ------------- | ------------- |
| JTW.CardLongerMKBar  | ImageAssetPath  | "@external:Data/Assets/Images/card.jpg"
| JTW.CardHeavierMKBar  | ImageAssetPath  | "@external:Data/Assets/Images/card.jpg"

`Name` 列是卡牌的`id`。 例如：`JTW.CardLongerMKBar`

`Key` 列是需要配置的卡牌属性，目前仅支持 `ImageAssetPath`

`Value` 列是对应的mod图片路径。注意需要加 `@external:` 前缀。比如图片位于 `mod`下的 `Data/Assets/Images/card.jpg`，需要对应填写：`"@external:Data/Assets/Images/card.jpg"`

### 卡牌id 查找
[悟空卡牌](card_wk.csv)

[白龙卡牌](card_wd.csv)

[唐僧卡牌](card_hm.csv)

[八戒卡牌](card_sk.csv)

## mod测试
   将自定义的`your_mod`放到游戏数据目录（需要手动创建`Mods`文件夹），如下：

   windows:
   ```
   %userprofile%\AppData\LocalLow\Z Studio\JTW\Mods\your_mod
   ```
   macOS:
   ```
   ~/Library/Application Support/Z Studio/JTW/Mods/your_mod
   ```
   重新启动`神州志西游`游戏进行测试。

## 上传mod 到steam 创意工坊

我们开发了一个用于上传mod到steam 创意工坊的程序，如下图所示。

![Alt text](uploader.jpg?raw=true)

下载创意工坊上传程序 [workshop_uploader](workshop_uploader.zip)

本程序包含两个主要功能：
1. 创建一个新的创意工坊
   - 在`输入创意工坊名称`的空白处，输入你的创意工坊名称 （内容不能空缺）
   - 在`输入创意工坊描述`的空白处，输入你的创意工坊内容描述
   - 在`输入创意工坊标签`的空白处，输入你所要添加的创意工坊标签
   - 鼠标左键点击`创意工坊文件地址`，选中你所要上传创意工坊内容的文件地址（文件地址需包含所有你要上传的文件）以mod样例举例，文件地址应为`test_mod`的地址；选中文件地址之后，空白处会显示文件地址的绝对路径
   - 鼠标左键点击`创意工坊封面地址`，选中你所要上传的创意工坊封面图片，选中图片地址之后，空白处会显示图片的绝对路径

完成之后，鼠标左键点击`创建创意工坊`，点击之后将会弹出`创新工坊上传中`的窗口，点击`OK`关闭窗口

![Alt text](uploading.png?raw=true)

上传创意工坊成功之后，将会弹出`上传创意工坊成功`的窗口 (如果上传的文件比较大，请耐心等待，期间不要关闭程序)

![Alt text](success.png?raw=true)

随后可以关闭`上传创意工坊成功`的窗口，创建创意工坊完成。

2. 更新已上传的创意工坊内容
   - 在`已上传创意工坊列表`中找到想要更新mod内容的条目，例如图中`神州志创意工坊`。鼠标左键点击创意工坊条目，创意工坊名称，描述和标签将会显示出来
   - 重复`创建创意工坊`的相同操作对创意工坊的内容进行修改


修改完之后点击`更新Mod内容`来进行更新，点击之后将会弹出上述操作相同`创新工坊上传中`的窗口，点击`OK`关闭窗口


上传创意工坊成功之后，将会弹出相同的`上传创意工坊成功`的窗口 (如果上传的文件比较大，请耐心等待，期间不要关闭程序)

随后可以关闭`上传创意工坊成功`的窗口，更新mod内容完成。

`注意：在使用该程序的之前，需要先登录steam账号。`