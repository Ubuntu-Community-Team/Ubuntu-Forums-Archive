---
title: "Nucleo for Metisse ./configure problem! Help!"
date: 2006-12-21
forum: Desktop Environments
---

### Post by psych787 on 2006-12-21
First of all, I will use any OS, Window Manager, _anything_ to get interactive scaled windows, so if you have a better idea how to do this I very much want to hear it! :cool:
My basic end goal is to get the same usability enhancement that NYDITOT Virtual Display gives my Pocket PC at any cost. As far as I know, Beryl and Compiz can't scale the windows and keep interactivity. The Metisse demo video shows that trick nicely...

That said, I've installed a bunch of things with apt-get and I do have all the right files in /usr/include/GL, but every time I run ./compile in the nucleo directory it ends like this:
```

psych787@merlin:~$ cd nucleo-0.1/
psych787@merlin:~/nucleo-0.1$ sudo ./configure
Password:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
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
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
appending configuration tag "F77" to libtool
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether byte ordering is bigendian... no
checking for dlopen in -ldl... yes
checking for X... no
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking for glFlush in -lGL... yes
checking for gluUnProject in -lGLU... yes
checking GL/glx.h usability... no
checking GL/glx.h presence... no
checking for GL/glx.h... no
configure: error: GL/GLU detected, but fail to found GLX (use CPPFLAGS?)

```
The 10 lines show some odd stuff. In particular:
Checking for X... no? Wtf, I'm running GNOME!
checking GL/glx.h usability... no Wtf, that file is there!
checking GL/glx.h presence... no Wtf, that file is there!
checking for GL/glx.h... no Wtf! that file is there!

I've dealt with a few errors already, but solved them all with google and sudo apt-get. I've also tried solving this by adding Load driv to xorg.conf and by reinstalling common-mesa-dev. Google can't seem to find an answer to this problem, and I've been stuck on this all day. ](*,) Any suggestions?

Update: I found some rpm packages and a guide, but after installing them GNOME didn't give me any really useful output as to why the newly created Metisse session didn't work. I've since moved on to either finding a way to configure Project Looking Glass and push back its windows and waiting for Beryl to get true input redirection. It'd still be nice if anyone could compile and run Metisse on Edgy and post a HowTo or even some binaries...

---

### Post by psych787 on 2006-12-21
*bump*
That was one quick bury... help please?

*update*
I have used the package that was made available for Edgy a while after this post. It works fine, and I simply cannot live without metisse anymore!

---

