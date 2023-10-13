# 微信公众号推送课表及天气

## 基础

### 简介

+ 作者：**申也**
+ 个人网站：[申也个人网站](www.dongshengye.space)
+ 个人公众号：**申也**
+ B站：**申也_**
+ 教学视频网址：

### 快速开始

克隆仓库到本地 `git clone https://gitee.com/dongshengye/wxPost.git`

#### JavaScript版

+ 在项目所在文件终端输入：`npm install`
+ 修改config.js配置文件
+ 运行index.js：`npm index.js`

#### python版

+ 在项目所在文件终端输入：`pip install -r requirements.txt`
+ 修改config.py配置文件
+ 运行main.py：`python main.js`



## 公众号测试号申请

### 申请测试号

1. 进入[微信公众平台接口测试帐号申请](https://mp.weixin.qq.com/debug/cgi-bin/sandbox?t=sandbox/login)，网址 https://mp.weixin.qq.com/debug/cgi-bin/sandbox?t=sandbox/login

2. 点击登录

   <img src="http://myimg.resumeg.club/markdown_img/image-20220915113429112.png" alt="image-20220915113429112" style="zoom:50%;" />

3. 登录成功进入控制台界面

   记录`app_id` `app_secret`

   <img src="http://myimg.resumeg.club/markdown_img/image-20220915113558716.png" alt="image-20220915113558716" style="zoom:67%;" />

4. 先用自己的手机扫测试号二维码，

   之后获得个人的`openid`

   ![image-20220915113844001](http://myimg.resumeg.club/markdown_img/image-20220915113844001.png)

5. 新增模板接口

   获得`template_id`

   ![image-20220915113959282](http://myimg.resumeg.club/markdown_img/image-20220915113959282.png)

   点击之后会让你填写模板内容。在这里放上我的模板内容

   ```
   今天是{{date.DATA}} 
   城市：{{city.DATA}} 
   天气：{{weather.DATA}} 
   最低气温: {{min_temperature.DATA}} 
   最高气温: {{max_temperature.DATA}} 
   今天是我们恋爱的第{{love_day.DATA}}天 
   距离墨墨的生日还有{{birthday.DATA}}天 -
   -------课表-------- 
   8-10 {{firstClass.DATA}} 
   10-12 {{secondClass.DATA}} 
   2-4 {{thirdClass.DATA}} 
   4-6 {{fourthClass.DATA}} 
   7-10 {{fifthClass.DATA}}
   ```

   最终结果为：

   <img src="http://myimg.resumeg.club/markdown_img/image-20220915114134077.png" alt="image-20220915114134077" style="zoom:50%;" />

   点击提交即可。

## 修改配置文件

### 配置文件展示

#### 不同语言配置文件对比

<img src="http://myimg.resumeg.club/markdown_img/1bad892d5c73a4968ae47fce40ef2318.png" style="zoom: 50%;" />

可以看到，JavaScript就多了一个 axios实例，以及声明变量用的const

#### 注意！

classes为课表目录，我定义的为一周七天，一天5节课

**但是，在python版本中是从周一开始。而JavaScript是从周日开始！**

### 微信公众号配置信息

#### 信息说明

`app_id`：测试号id

`app_secret`：测试号secret

`template_id`：测试号消息模板

`user/openid`：用户openid

#### 信息获取

请看公众测试号申请模板，其中有详细教学！

### 自定义配置信息

`province`：省份（获取天气用）

`city` ：城市（获取天气用）

`birthday` ：生日

`loveday` ：在一起的一天

`classes`：课表

#### 注意！

classes为课表目录，我定义的为一周七天，一天5节课

**但是，在python版本中是从周一开始。而JavaScript是从周日开始！**

## 获取服务器

### 购买服务器

在腾讯云、华为云、阿里云上都可以购买。

本教程以腾讯云为例。

进入[腾讯云官网](cloud.tencent.com)并购买**轻量应用服务器**

![image-20220915120924834](http://myimg.resumeg.club/markdown_img/image-20220915120924834.png)

### 选择服务器镜像

选择服务器镜像为宝塔面板

<img src="http://myimg.resumeg.club/markdown_img/image-20220915121136482.png" alt="image-20220915121136482" style="zoom: 67%;" />

### 进入自己的宝塔面板

在计划任务中添加如下配置

![image-20220918145148037](http://myimg.resumeg.club/markdown_img/image-20220918145148037.png)

之后，点击执行，并查看日志

![image-20220918145318697](http://myimg.resumeg.club/markdown_img/image-20220918145318697.png)

如果日志中有你想要的输出，证明成功！

----

<center>阅读到现在，你就已经可以配置好一个自动发送的测试号了，接下来进行<b>代码说明</b></center>

## 代码说明

### 流程说明

![未命名文件](http://myimg.resumeg.club/markdown_img/%E6%9C%AA%E5%91%BD%E5%90%8D%E6%96%87%E4%BB%B6.png)

### 技术说明

整体难度在**网络请求**，需要配置请求头去get和post。

业务逻辑难在对**日期的处理**上，但是有很多包可以去使用

同时，**课表的存储处理**还会考虑数据结构方面的知识！

## 后记

所有代码均已上传本人gitee！

