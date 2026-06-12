---
title: "compiling zsnes trouble"
date: 2008-12-23
forum: General Help
---

### Post by onlyliberty on 2008-12-23
I am a bit new to ubuntu and i am trying to compile zsnes by myself.  For some reason the one in the repository shows no activity when i click on the icon and in terminal spews out a bunch of numbers and stuff and says aborted.  So i figured i would give this a try.  I dled the tar file. extracted to the desktop.  Then in terminal i went to the src directory and the readme in the docs directory told me to type "sh ./autogen.sh

this is what happened

sh ./autogen.sh
Generating build information using aclocal and autoconf...
./autogen.sh: 6: aclocal: not found
./autogen.sh: 7: autoconf: not found
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for zlib - version >= 1.2.3... yes
checking for libpng - version >= 1.2.0... yes
checking if you want the zsnes debugger... yes
checking for initscr in -lcurses... yes
checking for initscr in -lncurses... yes
checking for initscr in -lpdcurses... no
checking if you want libao support... no
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for glGetError in -lGL... yes
checking for OpenGL... yes
checking for JMA support... yes
checking for cpu info... found
checking if you want gdb friendly executable... no
checking which cpu architecture to optimize for... native
checking if you want crazy optimizations... no
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
checking whether sys/types.h defines makedev... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged


ZSNES v1.51

SDL support                   Version 1.2.12
NASM support                  NASM version 2.03.01 compiled on Jun 19 2008
zlib support                  Version 1.2.3.3
PNG support                   Yes, version 1.2.27
OpenGL support                Yes
JMA support                   Yes
ZSNES debugger                Enabled

The binary will be installed in /usr/local/bin

Configure complete, now type 'make' and pray.

gokiburi@rounin:~/zsnes_1_51/src$ make
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__OPENGL__ -march=native -O3 -fomit-frame-pointer -s -fno-rtti -o tools/strutil.o -c tools/strutil.cpp
In file included from tools/strutil.cpp:22:
tools/strutil.h: In static member function ‘static int ci_char_traits::compare(const char*, const char*, size_t)’:
tools/strutil.h:34: error: ‘strncasecmp’ was not declared in this scope
make: *** [tools/strutil.o] Error 1
gokiburi@rounin:~/zsnes_1_51/src$ 
gokiburi@rounin:~/zsnes_1_51/src$ 

first of all i love the 'type 'make' and pray'

any ideas on what i am doing wrong?

---

### Post by onlyliberty on 2008-12-23
ok i installed autoconf and same thing happened

---

