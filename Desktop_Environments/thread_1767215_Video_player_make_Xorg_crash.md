---
title: "Video player make Xorg crash"
date: 2011-05-25
forum: Desktop Environments
---

### Post by GK N on 2011-05-25
Good day all,
i have upgrade my system from maveric to natty and i have install install the driver from Martins 
[http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html](http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html)
and since when i try to play a video (with mplayer gnompleplayer ou banshee) it makes Xorg crash and show me the login screen
need your help to fix it.
Thank in advance
Here is the result of the commande
```
 
./configure --prefix=/usr --disable-static
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
[COLOR=red]**checking whether to enable maintainer-specific portions of Makefiles... no**[/COLOR]
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
[COLOR=red]**checking whether we are cross compiling... no**[/COLOR]
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
[COLOR=red]**checking for g77... no**[/COLOR]
checking for f77... f77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether f77 accepts -g... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
[COLOR=red]**checking if gcc supports -fno-rtti -fno-exceptions... no**[/COLOR]
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
[COLOR=red]**checking whether to build static libraries... no**[/COLOR]
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
[COLOR=red]**checking whether to build static libraries... no**[/COLOR]
checking for f77 option to produce PIC... -fPIC
checking if f77 PIC flag -fPIC works... yes
checking if f77 static flag -static works... yes
checking if f77 supports -c -o file.o... yes
checking whether the f77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... /usr/bin/f77: Illegal option: -print-search-dirs
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for cpp... /usr/bin/cpp
checking if /usr/bin/cpp requires -undef... yes
checking if /usr/bin/cpp requires -traditional... yes
checking if XINERAMA is defined... yes
checking if RANDR is defined... yes
checking if RENDER is defined... yes
checking if XV is defined... yes
[COLOR=red]**checking if XF86MISC is defined... no**[/COLOR]
checking if DPMSExtension is defined... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... yes
checking for ANSI C header files... (cached) yes
checking for /usr/include/xorg/dri.h... yes
checking for /usr/include/xorg/sarea.h... yes
checking for /usr/include/xorg/dristruct.h... yes
checking whether to include DRI support... yes
checking for DRI... yes
[COLOR=red]**checking for /usr/share/X11/sgml/defs.ent... no**[/COLOR]
checking for linuxdoc... no
checking for ps2pdf... /usr/bin/ps2pdf
[COLOR=red]**checking Whether to build documentation... no**[/COLOR]
checking Whether to build pdf documentation... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/xvmc/Makefile
config.status: creating man/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

```

---

### Post by Shane10101 on 2011-07-10
I'm seeing the same issue. It doesn't matter whether I use VLC or Media Player:  When I open a video file (wmv or flv), the player opens & the cue bar starts moving.  No video is displayed & no audio plays.  After about 5 seconds, X crashes & the login screen opens.

This problem started only after I upgraded to Natty.  I'm not sure which log file I should check for crash info.  If someone will let me know, I'll post the relevant info here.

Thanks  :)

---

### Post by Shane10101 on 2011-07-10
Okay, in VLC, changing the output to X11 under Preferences > Video Settings works...but I don't know why.  

Here's where I found the fix:

[http://forum.eeeuser.com/viewtopic.php?id=16603](http://forum.eeeuser.com/viewtopic.php?id=16603)

How can I make this work for all video players.  (Not that I don't like VLC; I just want to know what the problem is!)

Thanks,

Shane

---

### Post by rivalarrival on 2011-08-04
Same problem - ever since the update to Natty, when I open a video in any player, Xorg restarts. 

Changing the output in VLC to X11 works.

---

