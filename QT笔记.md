QT
15分36，qq项目添加图标，资源文件在群内

改了资源文件，记得qmake一下
新建配置文件config.h方便以后更新修改数据

在.h文件中声明后 按alt+回车键，可以快速跳转到.cpp中实现空实现

添加资源文件步骤：1、右键项目->添加新文件->文件和类选：QT和Qt Resource File。选中。
                               2、打开项目文件路径，新建res文件夹，将复制好的资源文件粘贴进去
3、回到QT中，右键点击res.qrc，open in editor(以编辑的方式去打开)，添加前缀（区分不大就直接”/“），
添加文件把res文件夹中所有资源选中，打开。
4、构建一下，如果报out of memory allocating 1073745919 bytes，说明资源过大，需要用二进制的方式
找到res.qrc,按住shift+右键，打开终端命令窗口，输入rcc （在这之前要配置环境变量）
输入cls清屏，输入rcc -binary .\res.qrc -o plane.rcc    
回车，自动生成plane.rcc（原来80M的资源变17M了）

回到QT在main.cpp中添加QResource头文件，main函数中写QResource::registerResource()；
把plane.rcc文件拷贝到Debug同级目录下

回到配置头文件config.h中添加 #define GAME_RES_PATH "./plane.rcc"      //rcc文件路径
回到main.cpp添加config.h后就可以使用QResource::registerResource(GAME_RES_PATH);
主场景mainscene.cpp中
//加载图标
    setWindowIcon(QIcon(":/res/app.ico"));

工程文件中删除
RESOURCES += \
    res.qrc
就可以删除qrc转而使用rcc文件了



//命名规范
//类名首字母大写，单词和单词之间首字母大写
//函数名变量名称首字母小写，单词和单词之间首字母大写
//快捷键
//注释ctrl +l/运行ctrl + r编译ctrl +b
//字体缩放ctrl +鼠标滚轮/查找ctrl + f
//′整行移动ctrl + shift +或者↓/帮助文档F1
//自动对齐ctrl + i;
//同名之间的.h和.cpp切换F4
//帮助文档第一种方式F1 第二种左侧按钮第三种
//alt+shift+r 预览ui
f9添加断点，f5 运行程序
ctrl+shift+f 查找
