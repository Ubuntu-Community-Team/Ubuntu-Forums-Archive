---
title: "Gunrealtools GUTS"
date: 2006-07-23
forum: Gaming &amp; Leisure
---

### Post by Eazy© on 2006-07-23
Hi all!

Hope I put this thread in the right place.

I'm trying to install [gunrealtools]("http://gunrealtools.sourceforge.net/") but its not working. According to the install-readme I should install it with:
```
 ./autogen.sh && make
```
When I do this no makefile will be generated.

Here is the output I get:
```
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

processing .
Running libtoolize...
Running aclocal -I macros  ...
macros/linger.m4:4: warning: underquoted definition of AC_STRUCT_LINGER
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
macros/gnome-cxx-check.m4:2: warning: underquoted definition of GNOME_CHECK_CXX
macros/check-utmp.m4:11: warning: underquoted definition of AC_CHECK_UTMP
Running autoheader...
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader:
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows to define a template without
autoheader: WARNING: `acconfig.h':
autoheader:
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:             [Define if a function `main' is needed.])
autoheader:
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
Running automake --gnu  ...
Running autoconf ...
Running ./configure --enable-maintainer-mode --enable-compile-warnings ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/sh: /home/eazy/Sparas/UT2004/ut2004: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking if gcc supports -fno-rtti -fno-exceptions... no
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GNOME... Now type `make' to compile the package
make: *** Inga mål angavs och ingen makefil hittades.  Stannar. <== means, no makefil was found

```

I know I had this working in Hoary with Ubuntu, but I can remember how I got it to install. Now I'm using Kubuntu Dapper, and perhaps that is the problem as I dont have Gnome. Is Gnome required to install this? Anyone know of a solution, I would be most grateful.

Edit: one of the dependencis is (I think): libgtk2.0-dev + the ones in the install-readme and I have this installed.

---

### Post by Harleen on 2006-07-23
I also stumbled over this, what for me is a bug in the autogen script.
On the last message of autogen when it checks for GNOME there is no "yes" behind that check, which means, that this check failed. The script just doesn't tell you that it has failed and continues as if there was no error. You can take a look at config.log in the same directory to get more information.
For that error to disappear you need to install libgnome-dev. After that, I was able to build that programm and create a package for it: [gunrealtools_1.0-beta-0ubuntu1_i386.deb]("http://home.arcor.de/harleen/pakete/gunrealtools_1.0-beta-0ubuntu1_i386.deb")

---

### Post by Eazy© on 2006-07-23
Hi and thanx for the deb-package! It worked very well. I'll try to install libgnome-dev and se if I also can make a package just to see if I can by myselfe. Again, thanx for your answer and the package! :)

---

