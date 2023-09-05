## nvm 下载安装注意事项

1. 先卸载本机已安装的 node.js。
2. 下载 nvm，路径最好默认到 C 盘，也可自定义路径，但需配置系统和环境变量。

## nvm 安装步骤

1. 下载 [nvm-setup.zip](https://kgithub.com/coreybutler/nvm-windows/releases)
2. 解压安装包，双击打开 nvm-setup.exe
3. 选择安装目录，比如我的安装目录是 D:\Program\nvm
4. 选择 node 安装目录，比如我的安装目录是 D:\Program\nodejs
5. 点击下一步完成安装，在管理员权限下运行 PowerShell 输入如下命令，验证 nvm 是否安装成功。

```shell
nvm -v  // 验证nvm版本
```

## nvm 配置

打开 nvm 安装目录下的 settings.txt 文件，设置国内镜像（最新）[npmmirror 中国镜像站](https://npmmirror.com/)

```shell
node_mirror: https://npmmirror.com/mirrors/node/
npm_mirror: https://npmmirror.com/mirrors/npm/
```

## nvm 下载 nodejs

```shell
nvm install 14.17.2   // 下载指定node版本
node -v               // 验证node版本
npm -v                // 验证npm版本
nvm use 14.17.2       // 切换node
```

## 配置全局安装路径及缓存路径

PowerShell 输入如下命令进行配置

```shell
cd D:\Program\nvm   // 进入nvm安装目录,比如我的目录为 D:\Program\nvm
mkdir node_global           // 创建全局安装目录
mkdir node_cache            // 创建全局缓存目录
npm config set prefix "D:\Program\nvm\node_global"  //配置全局安装路径
npm config set cache "D:\Program\nvm\node_cache"    //配置全局缓存路径
```

打开此电脑 => 属性 => 高级系统设置 => 环境变量
用户变量：变量 Path 配置对应路径，更改为：D:\Program\nvm\node_global
系统变量：新建 NODE_PATH，添加：D:\Program\nvm\node_global\node_modules

设置 nodejs 淘宝镜像，并验证所有环境配置

```shell
npm config set registry https://registry.npmmirror.com/  // 设置国内镜像
npm config get registry                                  // 验证镜像
npm config ls                                            // 验证环境配置
```

## nvm 常用命令

```
nvm list available       //列出node可安装版本
nvm install --lts        //安装最新LTS版本
nvm install <version>    //安装指定版本
nvm install node         //安装最新node
nvm uninstall <version>  //卸载指定版本
nvm ls                   //查看已安装node版本
nvm use <version>        //切换node版本
```

## 卸载 nvm

1. 先删除你当初所安装的 nvm 的文件夹即可。
2. 文件夹内右键 此电脑 -- 点击属性 -- 找到高级系统设置 -- 环境变量。
3. 删除用户变量 和 系统变量中名为 NVM_HOME 和 NVM_SYMLINK 两个变量。其他的不要改。
4. 用户变量和系统变量中 path 中的 %NVM_HOME%;%NVM_SYMLINK% 两个属性，其他的不要改。

## 卸载 node.js

1. 打开 cmd 命令行窗口，输入 npm cache clean --force 回车执行
2. 打开系统自带的卸载功能，找到 node js 进行卸载。
3. 删除 C:\Users\Administrator\AppData\Roaming（有些系统路径为：C:\Users\admin\AppData\Roaming）文件下的 npm、npm-cache 或者如果是 zip 下载的安装包，直接删掉解压文件即可。
4. 删掉系统变量内有关 node 的，如果是 msi 安装是会自动删掉环境变量的。
5. 重启电脑，这一步主要目的是清除正在执行的 Node 进程，如果你能在任务管理器中手动清除 Node 进程也是可以的，但对于小白来说重启电脑是最好的操作。
6. 在 cmd 命令行中输入 where node 回车执行。如果有显示具体的目录，把这个目录删掉，以图中为例，这里我们就要删掉 D 盘下的 nodejs 文件夹，然后再重启。如果没有显示具体目录，说明已经卸载成功了。可以安心安装其他版本 node 了。
