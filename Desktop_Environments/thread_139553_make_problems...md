---
title: "make problems.."
date: 2006-03-04
forum: Desktop Environments
---

### Post by shinygerbil on 2006-03-04
Trying to install the latest version of Polyester [http://www.kde-look.org/content/show.php?content=27968](http://www.kde-look.org/content/show.php?content=27968) ; I configure it ok, then when I make it it runs configure again. Then I get some error messages:

```
Good - your configure finished. Start make now

steve@SteveUbuntu:~/src/polyester-0.8$ make
cd . && /bin/sh /home/steve/src/polyester-0.8/admin/missing --run aclocal-1.9
/usr/share/aclocal/gtk.m4:7: warning: underquoted definition of AM_PATH_GTK
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
 cd . && /bin/sh /home/steve/src/polyester-0.8/admin/missing --run automake-1.9 --gnu
cd . && perl admin/am_edit -padmin Makefile.in
cd . && rm -f configure
cd . && make -f admin/Makefile.common configure
make[1]: Entering directory `/home/steve/src/polyester-0.8'
make[1]: Leaving directory `/home/steve/src/polyester-0.8'
/bin/sh ./config.status --recheck
running /bin/sh ./configure  --prefix=/usr  --no-create --no-recursion
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
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
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wnon-virtual-dtor... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking if C++ programs can be compiled... yes
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... socklen_t
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking for poll in -lpoll... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking if res_init is available... yes
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking sizeof size_t == sizeof unsigned long... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... libraries /usr/X11R6/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for perl... /usr/bin/perl
checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... libraries /usr/lib, headers /usr/include/kde
checking if UIC has KDE plugins available... yes
checking for KDE paths... defaults
checking for dcopidl... /usr/bin/dcopidl
checking for dcopidl2cpp... /usr/bin/dcopidl2cpp
checking for mcopidl... /usr/bin/mcopidl
checking for artsc-config... /usr/bin/artsc-config
checking for kde-config... /usr/bin/kde-config
checking for meinproc... /usr/bin/meinproc
checking for kconfig_compiler... /usr/bin/kconfig_compiler
checking for dcopidlng... /usr/bin/dcopidlng
checking for xmllint... /usr/bin/xmllint
checking whether byte ordering is bigendian... no
checking for MAXPATHLEN... 4096
checking if client should be compiled... yes
checking if color-schemes should be compiled... yes
checking if style should be compiled... yes
configure: creating ./config.status

Good - your configure finished. Start make now

 /bin/sh ./config.status
fast creating Makefile
fast creating client/Makefile
fast creating client/config/Makefile
fast creating color-schemes/Makefile
fast creating style/Makefile
fast creating style/config/Makefile
config.pl: fast created 6 file(s).
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
cd . && /bin/sh /home/steve/src/polyester-0.8/admin/missing --run autoheader
rm -f stamp-h1
touch config.h.in
cd . && /bin/sh ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: Entering directory `/home/steve/src/polyester-0.8'
Making all in client
make[2]: Entering directory `/home/steve/src/polyester-0.8/client'
Making all in config
make[3]: Entering directory `/home/steve/src/polyester-0.8/client/config'
if /bin/sh ../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -MT polyesterconfig.lo -MD -MP -MF ".deps/polyesterconfig.Tpo" -c -o polyesterconfig.lo polyesterconfig.cc; \
then mv -f ".deps/polyesterconfig.Tpo" ".deps/polyesterconfig.Plo"; else rm -f ".deps/polyesterconfig.Tpo"; exit 1; fi
polyesterconfig.cc:25:26: error: configdialog.h: No such file or directory
polyesterconfig.cc:188:31: error: polyesterconfig.moc: No such file or directory
polyesterconfig.cc: In constructor 'polyesterConfig::polyesterConfig(KConfig*, QWidget*)':
polyesterconfig.cc:39: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:40: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:46: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:48: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:50: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:52: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:53: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:54: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:56: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:57: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:58: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:60: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc: At global scope:
polyesterconfig.cc:32: warning: unused parameter 'config'
polyesterconfig.cc:32: warning: unused parameter 'config'
polyesterconfig.cc: In destructor 'virtual polyesterConfig::~polyesterConfig()':
polyesterconfig.cc:71: warning: possible problem detected in invocation of delete operator:
polyesterconfig.cc:71: warning: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: warning: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:71: note: neither the destructor nor the class-specific operator delete will be called, even if they are declared when the class is defined.
polyesterconfig.cc: In member function 'void polyesterConfig::selectionChanged(int)':
polyesterconfig.cc:86: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:86: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:86: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:88: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:88: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:88: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc: In member function 'void polyesterConfig::load(KConfig*)':
polyesterconfig.cc:107: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:113: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:114: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:115: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:118: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:120: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:122: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:124: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:125: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:127: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc: In member function 'void polyesterConfig::save(KConfig*)':
polyesterconfig.cc:138: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:143: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:144: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:145: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:146: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:147: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:148: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:149: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:150: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:151: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc: In member function 'void polyesterConfig::defaults()':
polyesterconfig.cc:162: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:167: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:168: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:169: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:170: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:171: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:172: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:173: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:174: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
polyesterconfig.cc:175: error: invalid use of undefined type 'struct ConfigDialog'
polyesterconfig.h:36: error: forward declaration of 'struct ConfigDialog'
make[3]: *** [polyesterconfig.lo] Error 1
make[3]: Leaving directory `/home/steve/src/polyester-0.8/client/config'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/steve/src/polyester-0.8/client'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/steve/src/polyester-0.8'
make: *** [all] Error 2

```

Any help/suggestions appreciated. I had to install automake1.9 to get it this far; I've tried several times, re-dowloading the archive, making each section individually, but nothing has worked!

(or if anyone can find me a deb, I'd be grateful ;) - I know version 0.6.5 of this theme is in Dapper, but I don't want that!)

Thanks in advance

Steve

---

### Post by z-vet on 2006-03-04
I built it without problem. Check an attached file, there's a .deb inside it. Tell me if it works... :)

---

### Post by shinygerbil on 2006-03-04
Works perfectly :) thank you very much indeed!

Steve

---

### Post by z-vet on 2006-03-05
You're welcome. :)

---

