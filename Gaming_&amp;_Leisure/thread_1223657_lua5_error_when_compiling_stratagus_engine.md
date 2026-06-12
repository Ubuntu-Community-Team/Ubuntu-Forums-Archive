---
title: "lua5 error when compiling stratagus engine"
date: 2009-07-26
forum: Gaming &amp; Leisure
---

### Post by coolethan on 2009-07-26
```
ethan@ubuntu:~/Desktop/stargus/stratagus-2.2.4$ ./configure
checking for g++... g++
checking for C++ compiler default output... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for strcasestr... yes
checking for strnlen... yes
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for egrep... grep -E
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
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking png.h usability... yes
checking png.h presence... yes
checking for png.h... yes
checking bzlib.h usability... yes
checking bzlib.h presence... yes
checking for bzlib.h... yes
checking for main in -lbz2... yes
checking ogg/ogg.h usability... no
checking ogg/ogg.h presence... no
checking for ogg/ogg.h... no
checking vorbis/codec.h usability... no
checking vorbis/codec.h presence... no
checking for vorbis/codec.h... no
checking mikmod.h usability... no
checking mikmod.h presence... no
checking for mikmod.h... no
checking lua.h usability... yes
checking lua.h presence... yes
checking for lua.h... yes
checking for library containing lua_getfenv... no
configure: error: Lua5 is required
ethan@ubuntu:~/Desktop/stargus/stratagus-2.2.4$ 
```
i don't have all the dependencies yet but i have the latest version of lua installed (5.1.4) lua compiles and installes perfectly. i don't know what to do next.

---

### Post by Liolikas on 2009-07-26
What you are going to do whit it?
It is abandoned project devs now do BOSwars.

---

### Post by coolethan on 2009-07-26
i need it to play stargus. stargus 0.2 just recently came out

---

### Post by Liolikas on 2009-07-26
Try to find stratagus in synaptics.
Compiling is no joke: advanced task.

---

### Post by coolethan on 2009-07-26
> **Liolikas said:**
> Try to find stratagus in synaptics.
Compiling is no joke: advanced task.

i've done it before. anyways i got it working. i got the libvorbis-dev package from synaptic because i needed that anyways and now lua works. very strange :confused:

---

### Post by coolethan on 2009-07-26
all the dependencies are satisfied now but i get a new error upon the "make" command

```
src/video/movie.cpp: In function ‘int PlayMovie(const std::string&)’:
src/video/movie.cpp:308: error: ‘strstr’ was not declared in this scope
make: *** [src/video/obj/movie.o] Error 1

```

---

### Post by peppertarts on 2009-07-28
There is a bug in the current release that prevents Stratagus from building if you aren't compiling with Theora movie support. This has been fixed in the latest version which can be obtained from teh svn repository.

```
cd~/
svn co https://stratagus.svn.sourceforge.net/svnroot/stratagus/trunk stratagus
cd stratagus
./autogen
./configure
make
sudo make install
```

---

### Post by mattn2 on 2010-04-03
check out the svn and run 

debuild binary

in the trunk root. the same is true for wargus - i've added some debian package scripts to the svn some time ago.

---

