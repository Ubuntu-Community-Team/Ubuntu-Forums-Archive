---
title: "help configuring PCSX"
date: 2010-11-03
forum: Gaming &amp; Leisure
---

### Post by whitelightning2 on 2010-11-03
hey all im trying to configure pcsx and when it checks for glib-2, it says i dont have.  i checked synaptic and it says its installed but maybe its not the right version?  im not to sure whats going on here.

skippyjon@endurance:~$ '/home/skippyjon/Games/PS1/pcsx-df-1.10/configure'
.........
checking for GLIB2... no
configure: error: *** glib2 not found!
skippyjon@endurance:~$ 


skippyjon@endurance:~$ '/home/skippyjon/Games/PS1/pcsx-df-1.10/configure'
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking whether gcc and cc understand -c and -o together... yes
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
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
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
checking for ANSI C header files... (cached) yes
checking dependency style of gcc... gcc3
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ranlib... (cached) ranlib
checking for strerror in -lcposix... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking whether integer division by zero raises SIGFPE... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unsigned long long... yes
checking for inttypes.h... yes
checking whether the inttypes.h PRIxNN macros are broken... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for feof_unlocked... yes
checking for fgets_unlocked... yes
checking for getc_unlocked... yes
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
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for __fsetlocking... yes
checking for iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... yes
checking for LC_MESSAGES... yes
checking for bison... no
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... (cached) /usr/bin/msgmerge
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.1
checking for XML::Parser... ok
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB2... no
configure: error: *** glib2 not found!
skippyjon@endurance:~$

---

### Post by wingnux on 2010-11-04
You can always download the pre-compiled binary files from their website: [http://pcsx2.net/downloads.php?p=publicbeta](http://pcsx2.net/downloads.php?p=publicbeta)

---

### Post by Perfect Storm on 2010-11-04
Did you installed -dev of it?

---

### Post by thatguruguy on 2010-11-04
> **wingnux said:**
> You can always download the pre-compiled binary files from their website: [http://pcsx2.net/downloads.php?p=publicbeta](http://pcsx2.net/downloads.php?p=publicbeta)

He's trying to run pcsx, not pcsx2.

OP: Have you tried installing [PCSX-Reloaded]("http://pcsxr.codeplex.com/")?  It runs pretty well (at least on my system), and they have .deb files set up for both i386 and AMD64 systems for download [here]("http://pcsxr.codeplex.com/releases/view/50048").

---

