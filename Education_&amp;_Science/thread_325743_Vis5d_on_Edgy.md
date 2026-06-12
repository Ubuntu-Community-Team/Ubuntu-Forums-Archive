---
title: "Vis5d on Edgy"
date: 2006-12-26
forum: Education &amp; Science
---

### Post by vortmax on 2006-12-26
I'm attempting to install vis5d on Edgy.  The computer is a Intel laptop with radeon graphics.

I couldn't find a .deb package for vis5d on the universe or multiverse.  There was one under Warty, but nothing for any other versions.

I downloaded the source to compile it myself but run into an issue with the openGL drivers.  I get the following output from configure:

```

root@NixTop:/home/bealsm/Desktop/vis5d+-1.2.1# ./config
-bash: ./config: No such file or directory
root@NixTop:/home/bealsm/Desktop/vis5d+-1.2.1# ./configure
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for vendor's cc to be used instead of gcc... checking for cc... cc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix... 
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether cc accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of cc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for a BSD compatible install... /usr/bin/install -c
checking whether make sets ${MAKE}... (cached) yes
checking whether ln -s works... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependant libraries... pass_all
checking command to parse /usr/bin/nm -B output... ok
checking how to run the C preprocessor... cc -E
checking for dlfcn.h... yes
checking for ranlib... ranlib
checking for strip... strip
checking for objdir... .libs
checking for cc option to produce PIC... -fPIC
checking if cc PIC flag -fPIC works... yes
checking if cc static flag -static works... yes
checking if cc supports -c -o file.o... yes
checking if cc supports -c -o file.lo... 
checking if cc supports -fno-rtti -fno-exceptions... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
creating libtool
checking for libintl.h... yes
checking for ranlib... (cached) ranlib
checking for strerror in -lcposix... no
checking for ANSI C header files... yes
checking for cc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for off_t... yes
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking for argz.h... yes
checking for limits.h... yes
checking for locale.h... yes
checking for nl_types.h... yes
checking for malloc.h... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for sys/param.h... yes
checking for feof_unlocked... yes
checking for fgets_unlocked... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for stpcpy... yes
checking for strchr... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for libintl.h... (cached) yes
checking for GNU gettext in libc... yes
checking for dcgettext... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for bison... no
checking for catalogs to be installed...  pt_BR es
checking for db2html... ../missing db2html
checking for db2dvi... ../missing db2dvi
checking for db2ps... ../missing db2ps
checking for db2pdf... ../missing db2pdf
checking for db2rtf... ../missing db2rtf
checking for convert... no
configure: WARNING: ImageMagick convert program not found in path.  Convert can be used
to save vis5d pictures to a variety of output formats.
checking for f77... no
checking for xlf... no
checking for xlf77... no
checking for cf77... no
checking for fl32... no
checking for g77... no
checking for fort77... no
checking for f90... no
checking for xlf90... no
checking for g77... no
checking for f77... no
checking for xlf... no
checking for cf77... no
checking for cft77... no
checking for frt... no
checking for pgf77... no
checking for fl32... no
checking for af77... no
checking for fort77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for lf95... no
checking for g95... g95
checking whether we are using the GNU Fortran 77 compiler... no
checking whether g95 accepts -g... no
checking how to get verbose linking output from g95... configure: WARNING: compilation failed

checking for Fortran 77 libraries... 
checking for dummy main to link with Fortran 77 libraries... none
checking for Fortran 77 name-mangling scheme... 
configure: WARNING: unknown Fortran 77 name-mangling scheme
checking whether we are using gcc 2.90 or later... yes
*******************************************************
*       Congratulations! You are running Linux.       *
*******************************************************
checking whether cc accepts -malign-double... yes
checking whether cc accepts -mcpu=pentiumpro... no
checking whether cc accepts -mpentiumpro... yes
checking whether cc accepts -O3 -fomit-frame-pointer -malign-double -mpentiumpro... yes
checking for float... yes
checking size of float... 4
checking for int... yes
checking size of int... 4
checking for signed char... yes
checking size of signed char... 1
checking whether byte ordering is bigendian... no
checking for sqrt in -lm... yes
checking for strcasecmp... (cached) yes
checking for strncasecmp... yes
checking for strdup... (cached) yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for glBegin in -lGL... yes
checking for gluProject in -lGLU... no
checking for glBegin in -lMesaGL... no
couldn't find OpenGL libraries!
checking for bgnqstrip in -lgl_s... no
checking for PEXInitialize in -lPEX5... no
****************************************************
You need to install a 3D graphics library, preferably
the free OpenGL replacement, Mesa.  You can download
Mesa from the Mesa home page:
            http://www.mesa3d.org/
and install it by running:
       ./configure && make && su -c 'make install'
in the Mesa directory.
You may also need to run /sbin/ldconfig as root
to update the system after installing Mesa.
(First, add '/usr/local/lib' to /etc/ld.so.conf if
you installed Mesa under /usr/local, the default.)
****************************************************
configure: error: couldn't find 3D graphics library

```

So I use synaptic and find I have mesa already installed.  I go ahead and install the rest of the mesa related packages and run it again... does the same thing.   Apparently I don't have GL, GLU and MesaLG libraries, even though they are included in the Mesa package.  Also Vis5d is looking for the mesa install where it isn't located.  I can't seem to find where it is actually located on this install.

Any thoughts?

---

### Post by kleeman on 2006-12-26
Try installing the ati radeon gl packages: xorg-driver-fglrx and xorg-driver-fglrx-dev

---

### Post by vortmax on 2006-12-26
Okay,

I installed those packages and nothing.  So ran /sbin/ldconfig as was recomended in the output and rebooted.  Still I get the same error.

Is there some configuration I'm missing to enable openGL?

---

### Post by kleeman on 2006-12-26
You may need to specify manually where the opengl libraries and headers are. Check the contents of the packages I noted above to find out where they are then run ./configure --help to find out how to manually specify the paths.

---

### Post by kleeman on 2006-12-26
It compiled on my edgy system. You may wish to try installing the following packages as well:
libglu1-mesa
libglu1-mesa-dev
g77
g77-3.4
libnetcdfg-dev

Edit: Works fine with trial v5d files and animation of a 3d plot.

---

### Post by vortmax on 2006-12-26
> **kleeman said:**
> It compiled on my edgy system. You may wish to try installing the following packages as well:
libglu1-mesa
libglu1-mesa-dev
g77
g77-3.4
libnetcdfg-dev

Edit: Works fine with trial v5d files and animation of a 3d plot.

Thanks.  I (re)installed those packages and it compiled for me.  Not sure which on was causing the problem, but all works now.  Thanks.

---

### Post by quantum_guy on 2010-07-24
Just wanted to say thank you so much. I had the same problem and this worked for me. 

Thanks!

---

