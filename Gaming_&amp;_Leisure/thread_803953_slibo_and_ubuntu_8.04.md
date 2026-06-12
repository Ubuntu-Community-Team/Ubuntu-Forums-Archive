---
title: "slibo and ubuntu 8.04"
date: 2008-05-22
forum: Gaming &amp; Leisure
---

### Post by garrethdk on 2008-05-22
i downloaded slibo 0.4.4 and tried to run the configure , i got 
 sudo ./configure
[sudo] password for garreth: 
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.

any ideas how to make it work , i read somewhere that i need gcc and sqlite and ncurses and a couple more , but i checked these and there all there ?

---

### Post by atomkarinca on 2008-05-22
Have you tried installing build essentials? Open up a terminal (Applications > Accessories > Terminal) and type:

```
sudo apt-get install build-essential
```

---

### Post by garrethdk on 2008-05-28
downloaded and installed 
sudo apt-get install build-essential
then i got another error message so i downloaded the following
kdebase-dev
sqlite

there were no errors on the ./configure 
but the make gives 

make  all-recursive
make[1]: Entering directory `/home/garreth/Programs/slibo-0.4.4'
Making all in doc
make[2]: Entering directory `/home/garreth/Programs/slibo-0.4.4/doc'
Making all in .
make[3]: Entering directory `/home/garreth/Programs/slibo-0.4.4/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/garreth/Programs/slibo-0.4.4/doc'
Making all in en
make[3]: Entering directory `/home/garreth/Programs/slibo-0.4.4/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/garreth/Programs/slibo-0.4.4/doc/en'
make[2]: Leaving directory `/home/garreth/Programs/slibo-0.4.4/doc'
Making all in po
make[2]: Entering directory `/home/garreth/Programs/slibo-0.4.4/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/garreth/Programs/slibo-0.4.4/po'
Making all in src
make[2]: Entering directory `/home/garreth/Programs/slibo-0.4.4/src'
Making all in sliboengine
make[3]: Entering directory `/home/garreth/Programs/slibo-0.4.4/src/sliboengine'
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT -std=gnu99 -DUSE_ASM -DMYDEBUG -W -Wall -Wchar-subscripts -Wshadow -Wpointer-arith -Wmissing-prototypes -Wwrite-strings -D_XOPEN_SOURCE=500 -D_GNU_SOURCE -O2   -Wformat-security -Wmissing-format-attribute -MT board.o -MD -MP -MF ".deps/board.Tpo" \
	  -c -o board.o `test -f 'board.c' || echo './'`board.c; \
	then mv -f ".deps/board.Tpo" ".deps/board.Po"; \
	else rm -f ".deps/board.Tpo"; exit 1; \
	fi
In file included from board.c:15:
main.h:14:21: error: ncurses.h: No such file or directory
In file included from board.c:15:
main.h:18: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘computerTurn’
main.h:19: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pondering’
main.h:20: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pondermode’
main.h:21: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘stopSearch’
main.h:30: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
main.h:36: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘stopped’
main.h:44: error: expected specifier-qualifier-list before ‘bool’
In file included from board.c:16:
util.h:54: error: expected ‘)’ before ‘*’ token
util.h:59: error: expected ‘)’ before ‘*’ token
util.h:60: error: expected ‘)’ before ‘*’ token
board.c: In function ‘undoMove’:
board.c:405: error: ‘bool’ undeclared (first use in this function)
board.c:405: error: (Each undeclared identifier is reported only once
board.c:405: error: for each function it appears in.)
board.c:405: error: expected ‘;’ before ‘found’
board.c:408: error: ‘found’ undeclared (first use in this function)
board.c:408: error: ‘true’ undeclared (first use in this function)
make[3]: *** [board.o] Error 1
make[3]: Leaving directory `/home/garreth/Programs/slibo-0.4.4/src/sliboengine'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/garreth/Programs/slibo-0.4.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/garreth/Programs/slibo-0.4.4'
make: *** [all] Error 2


any ideas ?

---

