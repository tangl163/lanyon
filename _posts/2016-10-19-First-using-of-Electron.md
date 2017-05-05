---
layout: post
title: "The first using of Electron"
date: 2016-11-03 20:35:45 -0800
excerpt_separator: <!--more-->
---

### Electron 第一次调研报告

1. Electron 是什么？  
Electron 是由 GitHub 开发的开源框架，框架使用网页作为用户界面，框架中集成了 Node.js 和 Chromium 浏览器。 所以我们可以把 Electron 看成是一个由 JavaScript 控制的浏览器。

2. Electron 能做什么？  
我们可以像开发 Web 应用程序一样，用其开发桌面应用程序。 也就是说，Web 应用程序能做的，Electron 都能做，只不过 Electron 把注意力集中在桌面应用程序上。

3. 创建第一个 Electron 应用程序  
    ● 首先安装 [Node.js](https://nodejs.org/en/)  
    ● 在命令行运行 `npm install electron -g`
    ● 在任意一个文件夹（我们的文件夹名叫 **_demo_** ）下分别建立 "package.json" "main.js" "index.html" 这三个文件


目录结构如下

```
demo/
├── package.json
├── main.js
└── index.html
```

<!--more-->

package.json 文件内容如下

```json
{
    "name": "demo-demo",
    "main": "main.js",
    "version": "1.0"
}
```


main.js 文件内容如下
```js
const electron = require('electron');
const app = electron.app;
const BrowserWindow = electron.BrowserWindow;

var mainWindow = null;

function createWindow()
{
    mainWindow = new BrowserWindow({width: 400, height: 300});

    mainWindow.loadURL(`file://${__dirname}/index.html`);

    mainWindow.on('closed', () => {mainWindow = null;});
}

app.on('ready', createWindow);

app.on('window-all-closed', () => {
    if (process.platform !== 'darwin') {
        app.quit();
    }
});
```

index.html 文件内容如下

```html
<!DOCTYPE html>
<html>
<head>
    <title>Demo</title>
</head>
<body>
    <h1>Hello, demo.</h1>
</body>
</html>
```

大功告成！

**现在切换到demo目录下，运行 `electron .` 即可启动应用程序**

4. 下一阶段目标  
熟悉 Electron 的其他接口应用。

