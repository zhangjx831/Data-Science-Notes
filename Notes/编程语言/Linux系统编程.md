## Linux编程



## Makefile

1.基础

一个工程中的源文件不计数，其按**类型、功能、模块**分别放在若干个目录中，makefile定义了一系列的规则来指定，哪些文件需要先编译，哪些文件需要后编译，哪些文件需要重新编译，甚至于进行更复杂的功能操作

通常一个项目的执行分成四个部分

**预处理：**写好的高级语言的程序文本比如hello.c,预处理器根据#开头的命令，修改原始的程序，如#include<stdio.h>,将把系统中的头文件插入到程序文本中，通常是以.i结尾的文件

**编译阶段：**编译器将hello.i文件翻译成文本文件*hello.s,这个是汇编语言程序。高级语言是源程序。所以注意概念之间的区别。汇编语言程序干嘛？每条语句都以标准的文本格式确切描述一条低级机器语言指令。*不同的高级语言翻译的汇编语言相同

**汇编阶段：**汇编器将hello.s翻译成机器语言指令。把这些指令打包成可重定位目标程序，即.o文件。hello.o是一个二进制文件，它的字节码是机器语言指令，不再是字符。前面两个阶段都还有字符

**链接阶段：**比如hello程序调用printf程序，它是每个C编译器都会提供的标准库C的函数。这个函数存在于一个名叫printf.o的单独编译好的目标文件中，这个文件将以某种方式合并到hello.o中。链接器就负责这种合并。得到的是可执行目标文件

2.makefile组成

target    - 目标文件, 可以是 Object File, 也可以是可执行文件

prerequisites - 生成 target 所需要的文件或者目标

command    - make需要执行的命令 (任意的shell命令), Makefile中的命令必须以 [tab] 开头

语法如下所示：

target ... : prerequisites ...
   command
   …

 