---
title: "Install Allacrost Latest Release - Demo Version 0.2.2"
date: 2010-03-12
forum: Gaming &amp; Leisure
---

### Post by Kdar on 2010-03-12
[http://www.allacrost.org/download](http://www.allacrost.org/download)

I was trying to install this game from source package.

But when I try to install this, I get this out put:

> [armen@armen-desktop allacrost-02282010]$ ./configure && make && make install
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking whether to enable -O3 compiler optimization... yes
checking whether to enable debugging... no
checking for X... no
checking whether to enable usage of map editor... yes
checking for Qt4 headers... no
checking for Qt4 libraries... no
configure: error: in `/home/armen/Desktop/allacrost-02282010':
configure: error: Qt4 development libraries not found
See `config.log' for more details.


It can't get installed because of this? and what can I do to fix it?
> configure: error: in `/home/armen/Desktop/allacrost-02282010':
configure: error: Qt4 development libraries not found

---

### Post by Asraniel on 2010-03-12
install libqt4-dev

---

### Post by Kdar on 2010-03-12
Thanks. that helped...

but now I have another error:
> Now type 'make'.

moc-qt4 -o src/editor/dialog_boxes.moc.cpp src/editor/dialog_boxes.h
moc-qt4 -o src/editor/editor.moc.cpp src/editor/editor.h
moc-qt4 -o src/editor/grid.moc.cpp src/editor/grid.h
moc-qt4 -o src/editor/skill_editor.moc.cpp src/editor/skill_editor.h
moc-qt4 -o src/editor/tileset_editor.moc.cpp src/editor/tileset_editor.h
make  all-recursive
make[1]: Entering directory `/home/armen/Desktop/allacrost-02282010'
Making all in txt
make[2]: Entering directory `/home/armen/Desktop/allacrost-02282010/txt'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/armen/Desktop/allacrost-02282010/txt'
make[2]: Entering directory `/home/armen/Desktop/allacrost-02282010'
g++ -DHAVE_CONFIG_H -I. -I/usr/include/SDL -I/usr/include/AL -I/usr/include/lua5.1 -I./src -I./src/engine -I./src/engine/audio -I./src/engine/video -I./src/engine/script -I./src/global -I./src/common -I./src/common/global -I./src/common/gui -I./src/modes -I./src/modes/battle -I./src/modes/boot -I./src/modes/map -I./src/modes/menu -I./src/modes/save -I./src/modes/shop -DDATADIR=\"/usr/local/share/games/allacrost\" -DLOCALEDIR=\"/usr/local/share/games/allacrost/txt\" -DPACKAGE=\"allacrost\" -I/usr/X11R6/include -Wall -O3 -I/usr/include/qt4 -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/Qt3Support -DQT_CLEAN_NAMESPACE -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT3_SUPPORT -DQT_SHARED -Wall -O3 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o `test -f 'src/main.cpp' || echo './'`src/main.cpp
src/main.cpp: In function ‘int main(int, char**)’:
src/main.cpp:358: warning: ignoring return value of ‘int chdir(const char*)’, declared with attribute warn_unused_result
src/main.cpp: At global scope:
src/main.cpp:419: fatal error: opening dependency file .deps/main.Tpo: Permission denied
compilation terminated.
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/armen/Desktop/allacrost-02282010'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/armen/Desktop/allacrost-02282010'
make: *** [all] Error 2


---

