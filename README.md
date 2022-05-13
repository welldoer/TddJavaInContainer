# TddJavaInContainer

准备容器环境，参考：
1. [在VS Code中使用带Docker容器的Java开发环境 – Bruno Borge](https://www.jdon.com/52203)

具体步骤：
1. 在 GitHub 中创建新的 repository；
2. 在本机执行 git clone；
3. 打开 Vscode，点击菜单“查看”下"命令面板"，以 Remote-Containers: Open Folder in Container 方式打开项目；
4. 依据提示，选择 OS，并增加 Maven、Gradle、Node、Git 等必要安装软件，等待容器镜像生成；
  a) 若选择 alpine，则容器镜像较小，建议修改 dockerfile 来自动安装软件：
    1) 编辑 .devcontainer/Dockerfile，将 apk 安装注释取消、采用 sudo 方式、安装 openjdk11 gradle python3-dev
  b) 若选择 alpine，也可以手动安装软件
    1) sudo apk add openjdk11 gradle python3-dev
    2) 在用户 .bashrc、.zshrc 中增加：
       export JAVA_HOME="/usr/lib/jvm/java-11-openjdk"
       export PATH="${PATH}:${JAVA_HOME}/bin"
    3) 退出 bash 或 zsh，重新登入
5. 执行 java -version、mvn --version、gradle --version、node -v、npm -v、git --version 检查；
6. 提交更新至 repository；