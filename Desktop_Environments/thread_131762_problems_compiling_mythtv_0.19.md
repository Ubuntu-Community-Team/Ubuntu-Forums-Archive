---
title: "problems compiling mythtv 0.19"
date: 2006-02-17
forum: Desktop Environments
---

### Post by zeltak on 2006-02-17
i am having problem compiling myth 0.19. i am using hyamns excellent guide
([http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)) and have some problems, firstly when i try to use the ./configure command i get an error:

./configure --with-prefix=/usr/local/mythtv-0.19
Unknown option "--with-prefix=/usr/local/mythtv-0.19".
See ./configure --help for available options.

so i used ./configure --prefix=/usr/local/mythtv-0.19

and it seemed to work for the mythtv install, is that ok?

then i again got stuck at the make part of mythtv plugins. i used the command: ./configure --prefix=/usr/local/mythtv-0.19 --enable-transcode --enable-vcd

and then ran make

root@ztpc:/opt/src/mythplugins-0.19# make
cd mythbrowser && make -f Makefile
make[1]: Entering directory `/opt/src/mythplugins-0.19/mythbrowser'
cd mythbrowser && make -f Makefile
make[2]: Entering directory `/opt/src/mythplugins-0.19/mythbrowser/mythbrowser'
g++ -c -pipe -Wall -W -fomit-frame-pointer -D_REENTRANT -D_GNU_SOURCE -DPREFIX=\"\" -D_FILE_OFFSET_BITS=64 -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/include -I/usr/kde/3.3/include -I/include -I/usr/include/kde -I/opt/kde3/include -I/usr/include/qt3 -o main.o main.cpp
main.cpp:20:30: error: mythtv/exitcodes.h: No such file or directory
main.cpp: In function 'int main(int, char**)':
main.cpp:90: error: 'FRONTEND_EXIT_NO_MYTHCONTEXT' was not declared in this scope
main.cpp:96: error: 'FRONTEND_EXIT_DB_ERROR' was not declared in this scope
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/opt/src/mythplugins-0.19/mythbrowser/mythbrowser'
make[1]: *** [sub-mythbrowser] Error 2
make[1]: Leaving directory `/opt/src/mythplugins-0.19/mythbrowser'
make: *** [sub-mythbrowser] Error 2

what am i doing wrong i used all the steps in guide exactly...any ideas?


thx alot
zeltak is online now 	Edit/Delete Message

---

### Post by nikopol on 2006-02-17
Not sure exactly what you're doing wrong but there are pre-compiled packages of MythTV: 
see here:
[http://ubuntuforums.org/showthread.php?t=130099](http://ubuntuforums.org/showthread.php?t=130099)

---

