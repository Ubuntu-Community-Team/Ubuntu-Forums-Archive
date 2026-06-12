---
title: "Pidgin bot sentry"
date: 2010-04-12
forum: Desktop Environments
---

### Post by SNOOPY817 on 2010-04-12
I been trying to get the Bot-Sentry to work but I haven't been able to get it to work I keep getting error's on terminal..

```

snoopy@snoopy-desktop:~/Desktop/bot-sentry-1.3.0$ ./configure --libdir=/usr/lib
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for prefix by checking for pidgin... /usr/bin/pidgin
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
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
checking whether to build static libraries... no
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
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for intltool >= 0.40.0... 0.40.6 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for head... /usr/bin/head
checking for makensis... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.15.0... yes
checking for purple... yes
checking purple_CFLAGS... -I/usr/include/libpurple -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking purple_LIBS... -lpurple -lglib-2.0  
checking PURPLE_VERSION... 2.5.5
checking PURPLE_MAJOR_VERSION... 2
checking purple_prefix... /usr
checking purple_exec_prefix... /usr
checking purple_libdir... /usr/lib
checking plugindir... /usr/lib/purple-2
checking locale_CPPFLAGS... -DLOCALEDIR=\"$(prefix)/$(DATADIRNAME)/locale\"
checking for library containing g_get_current_time... none required
checking for library containing purple_account_get_connection... none required
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking glib.h usability... yes
checking glib.h presence... yes
checking for glib.h... yes
checking plugin.h usability... yes
checking plugin.h presence... yes
checking for plugin.h... yes
checking for version.h... yes
checking for util.h... yes
checking debug.h usability... yes
checking debug.h presence... yes
checking for debug.h... yes
checking for account.h... yes
checking accountopt.h usability... yes
checking accountopt.h presence... yes
checking for accountopt.h... yes
checking for privacy.h... yes
checking for an ANSI C-conforming const... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating po/Makefile.in
config.status: creating po/Makevars
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
configure: === bot-sentry 1.3.0 configured installation directories ===
configure:     prefix      = /usr
configure:     exec_prefix = ${prefix}
configure:     libdir      = /usr/lib
configure:     plugindir   = /usr/lib/purple-2
configure:     datarootdir = ${prefix}/share
configure:     itlocaledir = /usr/share/locale
configure: === bot-sentry 1.3.0 configured installation directories ===
checking if bot-sentry libdir and purple libdir are the same... yes
snoopy@snoopy-desktop:~/Desktop/bot-sentry-1.3.0$ make
make  all-recursive
make[1]: Entering directory `/home/snoopy/Desktop/bot-sentry-1.3.0'
Making all in po
make[2]: Entering directory `/home/snoopy/Desktop/bot-sentry-1.3.0/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/snoopy/Desktop/bot-sentry-1.3.0/po'
make[2]: Entering directory `/home/snoopy/Desktop/bot-sentry-1.3.0'
make[2]: Leaving directory `/home/snoopy/Desktop/bot-sentry-1.3.0'
make[1]: Leaving directory `/home/snoopy/Desktop/bot-sentry-1.3.0'
snoopy@snoopy-desktop:~/Desktop/bot-sentry-1.3.0$ 


```

Anyone know the problem? Maybe because I'm on a older version of Pidgin?

---

