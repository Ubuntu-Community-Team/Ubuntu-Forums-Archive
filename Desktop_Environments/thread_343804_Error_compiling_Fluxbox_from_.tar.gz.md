---
title: "Error compiling Fluxbox from .tar.gz"
date: 2007-01-22
forum: Desktop Environments
---

### Post by Maelgwyn on 2007-01-22
Hi all,

I've downloaded and extracted the latest fluxbox .tar.gz which was fine, but when I try to ./configure, I get an error and then it kicks me out of the process... I've included the whole output of the ./configure, just to make sure it's not something earlier on! :)

```

haakuturi@whakatane:~/Desktop/fluxbox-1.0rc2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/haakuturi/Desktop/fluxbox-1.0rc2/missing: Unknown `--run' option
Try `/home/haakuturi/Desktop/fluxbox-1.0rc2/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking for correct ltmain.sh version... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for sed... sed
checking for ANSI C header files... (cached) yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking libgen.h usability... yes
checking libgen.h presence... yes
checking for libgen.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking process.h usability... no
checking process.h presence... no
checking for process.h... no
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking stdarg.h usability... yes
checking stdarg.h presence... yes
checking for stdarg.h... yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/signal.h usability... yes
checking sys/signal.h presence... yes
checking for sys/signal.h... yes
checking for sys/stat.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for sys/types.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking iconv.h usability... yes
checking iconv.h presence... yes
checking for iconv.h... yes
checking sstream usability... yes
checking sstream presence... yes
checking for sstream... yes
checking cassert usability... yes
checking cassert presence... yes
checking for cassert... yes
checking cctype usability... yes
checking cctype presence... yes
checking for cctype... yes
checking cerrno usability... yes
checking cerrno presence... yes
checking for cerrno... yes
checking cmath usability... yes
checking cmath presence... yes
checking for cmath... yes
checking cstdarg usability... yes
checking cstdarg presence... yes
checking for cstdarg... yes
checking cstdio usability... yes
checking cstdio presence... yes
checking for cstdio... yes
checking cstdlib usability... yes
checking cstdlib presence... yes
checking for cstdlib... yes
checking cstring usability... yes
checking cstring presence... yes
checking for cstring... yes
checking ctime usability... yes
checking ctime presence... yes
checking for ctime... yes
checking whether time.h and sys/time.h may both be included... yes
checking for basename... yes
checking for getpid... yes
checking for setlocale... yes
checking for sigaction... yes
checking for strcasestr... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for catopen... yes
checking for catgets... yes
checking for catclose... yes
checking for strftime... yes
checking for iconv_open in -liconv... no
checking for libiconv_open in -liconv... no
checking for iconv declaration... no
checking for t_open in -lnsl... no
checking for socket in -lsocket... no
checking for X... no
configure: error: Fluxbox requires the X Window System libraries and headers.

```

Can anyone help? This is a fresh Edgy install with Gnome, so I thought I'd have the X Window System libs & headers??

---

### Post by danhm on 2007-01-22
You probably need the development headers.


```

sudo apt-get libx11-dev
```

That should do it.


Is the package in the repository out of date? It is probably much less of a hassle to install Fluxbox from that.

---

### Post by Maelgwyn on 2007-01-22
=( That didn't work... 

I don't think it's out of date in the repo's, I just want to have done it from scratch lol

---

### Post by Mike_Longbow on 2007-01-22
The problem in here is that you need to have installed the X Window System (including its development files) before installing any window manager such as fluxbox... Are you running a server??? Or do you have any other graphical interface (gnome, xfce, kde)???
Anyway, before compiling, try with:
```
sudo apt-get install x-window-system-core
```

---

### Post by Mike_Longbow on 2007-01-22
> **danhm said:**
> You probably need the development headers.


```

sudo apt-get libx11-dev
```

That should do it.


Is the package in the repository out of date? It is probably much less of a hassle to install Fluxbox from that.

Oh, and I think that line should be more like this:
```
sudo apt-get install libx11-dev
```
...don't you? :wink:

---

