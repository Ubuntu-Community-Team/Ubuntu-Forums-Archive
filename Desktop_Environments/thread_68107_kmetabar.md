---
title: "kmetabar"
date: 2005-09-22
forum: Desktop Environments
---

### Post by f1dave on 2005-09-22
Hello all,

Just interested to see if other kubuntu users have managed to get kmetabar ([http://www.kde-look.org/content/show.php?content=28725](http://www.kde-look.org/content/show.php?content=28725)) to work? I'm having some makefile problems myself...

---

### Post by Paulus on 2005-09-22
Hey, I've been having problems with that exact metabar too!   I have succesfully compiled and make make installed it, but it doesn't show up when I try and add it.
:s
what errors are you getting?

---

### Post by f1dave on 2005-09-22
```
meacod01@formula1:~/downloads/kmetabar-0.2/kmetabar$ make -f Makefile.cvs
This Makefile is only for the CVS repository
This will be deleted before making the distribution

*** Creating acinclude.m4
*** Creating list of subdirectories
*** Creating configure.in
*** Creating aclocal.m4
*** Creating configure
*** Creating config.h template
*** Creating Makefile templates
src/Makefile.am:11: variable `taglib_libs' not defined
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
```

That's the problem there.

---

### Post by Paulus on 2005-09-22
This might be sound really dumb, but when i compiled it all i did was
 ```
./configure
make
sudo make install
``` 

no doubt that why I can't get it working, can't help you with that error my friend :neutral:

---

### Post by Knome_fan on 2005-09-22
> make -f Makefile.cvs 

I'd guess that this is the problem.

If I understand you right, you aren't using the cvs version, but the beta release, so you don't need this step, but only have to run ./configure and then make, as Paulus did.

On tip though, you might want to use sudo checkinstall (you'll have to install it first of course), instead of simply make install, as checkinstall will build a .deb package for you, which is cleaner than simply installing it.

---

### Post by Paulus on 2005-09-22
hey, what do we do once it's sucessfully installed?   I can't get it to show up.... It is supposed to be an option when you click on the left hand bar as an external plugin?

btw, i'm running kde 3.5 beta, which apparently has it's own nice metabar, which i can't seem to see, any help lol

---

### Post by f1dave on 2005-09-22
[QUOTE=Knome_fan]I'd guess that this is the problem.
[/QUOTE]

Bah, i'm a fool. Thanks, now i'll try installing it like that.

---

### Post by f1dave on 2005-09-22
[QUOTE=Paulus]hey, what do we do once it's sucessfully installed?   I can't get it to show up.... It is supposed to be an option when you click on the left hand bar as an external plugin?

btw, i'm running kde 3.5 beta, which apparently has it's own nice metabar, which i can't seem to see, any help lol[/QUOTE]

Yes, i too cant seem to get it to show now that it is installed. :S
KDE 3.4.2 here

---

### Post by Paulus on 2005-09-22
can anyone shed any light on this?

---

### Post by Knome_fan on 2005-09-22
It works for me here.

Just a guess, but iirc I installed it with ./configure --prefix=/usr (If you do this, use checkinstall!). Probably the default install location is /usr/local and /usr/local might not be in your $PATH, so that KDE can't find it.

Again, I'm just guessing here.

---

### Post by Paulus on 2005-09-22
genuis!!!!!!!!1

it works now, and i've learnt stuff too!
here's how I did it:
 ```
sudo apt-get install checkinstall
./configure --prefix=/usr
make
sudo checkinstall
at the end, remeber to change the version to an integer
install the deb
be happy :)
``` 

thanks knome_fan!

---

### Post by f1dave on 2005-09-22
Yep, works here too. Rock on. Thanks all!

---

### Post by drizek on 2005-09-23
just to clarify, there is no metabar by default in kde 3.5

---

### Post by raven on 2005-10-05
I still can not get to install
I do ./configure --prefix=/usr
it gives me the message "Good - your configure finished. Start make now"
I do make I get these errors
"metabar.h: At global scope:
metabar.h:22: error: virtual outside class declaration
metabar.h:24: error: parse error before `protected'
metabar.h:30: error: parse error before `}' token"
around 20 of them
and then these around 20 of them 
"metabar.moc: In member function `bool Metabar::qt_emit(int, QUObject*)':
metabar.moc:82: error: parse error before `::' token
metabar.moc:81: warning: unused parameter `int _id'
metabar.moc:81: warning: unused parameter `QUObject*_o'"

and last lines I have these
"make[2]: *** [metabar.lo] Error 1
make[2]: Leaving directory `/home/username/Desktop/metabar-0.8/metabar/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/username/Desktop/metabar-0.8/metabar'
make: *** [all] Error 2"
if I do sudo checkinstal I will get the error around 10 of them
"metabar.cpp:54: warning: unused parameter `QObject*par'
metabar.cpp:54: warning: unused parameter `QWidget*widp'
metabar.cpp:54: warning: unused parameter `QString&desktopname'
metabar.cpp:54: warning: unused parameter `const char*name'"

do I need some special packages that I have to install before metabar
I have KDE 3.4.2 kubuntu
 after sudo checkinstall 
I get this 
"make[1]: *** [metabar.lo] Error 1
make[1]: Leaving directory `/home/username/Desktop/metabar-0.8/metabar/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye."

I posted just a sample of the errors cause I have a lot of them
with different output
any help ?

---

### Post by Knome_fan on 2005-10-06
Hm, I just tried to compile the new beta2 and it worked like a charm here.

Could you post the output prior to your second code snippet (that is to  make[2]: *** [metabar.lo] Error 1).

It should normally say what is wrong before it bails out like this.

---

### Post by raven on 2005-10-06
I got metabar from here [http://www.kde-apps.org/content/show.php?content=28725&PHPSESSID=d1f41db96a303267765c036ac95e0ff4](http://www.kde-apps.org/content/show.php?content=28725&PHPSESSID=d1f41db96a303267765c036ac95e0ff4) it's the beta2
I do ./configure --prefix=/usr
I get "Good - your configure finished. Start make now"

here is the output of ./configure --prefix=/usr

---------------[debut of ./configure output]-------------
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
checking for X... libraries /usr/X11R6/lib, headers /usr/X11R6/include
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
checking if doc should be compiled... yes
checking if po should be compiled... yes
checking if src should be compiled... yes
configure: creating ./config.status
fast creating Makefile
fast creating doc/Makefile
fast creating doc/en/Makefile
fast creating po/Makefile
fast creating src/Makefile
config.pl: fast created 5 file(s).
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

Good - your configure finished. Start make now
-------------[END of ./configure output]---------------

I do "make" these all the errors that I get

---------------[debut of errors : make]--------------------
"make  all-recursive
make[1]: Entering directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar'
Making all in doc
make[2]: Entering directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc'
Making all in .
make[3]: Entering directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc'
Making all in en
make[3]: Entering directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc/en'
/usr/bin/meinproc --check --cache index.cache.bz2 ./index.docbook
make[3]: Leaving directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc/en'
make[2]: Leaving directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc'
Making all in po
make[2]: Entering directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/po'
Making all in src
make[2]: Entering directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/src'
/usr/share/qt3/bin/moc ./kmetabar.h -o kmetabar.moc
if /bin/sh ../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I/usr/X11R6/include  -I/usr/include/kde/arts   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT kmetabar.lo -MD -MP -MF ".deps/kmetabar.Tpo" -c -o kmetabar.lo kmetabar.cpp; \
then mv -f ".deps/kmetabar.Tpo" ".deps/kmetabar.Plo"; else rm -f ".deps/kmetabar.Tpo"; exit 1; fi
In file included from kmetabar.cpp:5:
kmetabar.h:8:31: konqsidebarplugin.h: No such file or directory
In file included from kmetabar.cpp:5:
kmetabar.h:16: error: parse error before `{' token
kmetabar.h:17: error: virtual outside class declaration
kmetabar.h:17: error: non-member function `const char* className()' cannot have
   `const' method qualifier
kmetabar.h:17: error: virtual outside class declaration
kmetabar.h:17: error: virtual outside class declaration
kmetabar.h:17: error: virtual outside class declaration
kmetabar.h:17: error: virtual outside class declaration
kmetabar.h: In function `QObject* qObject()':
kmetabar.h:17: error: invalid use of `this' in non-member function
kmetabar.h: At global scope:
kmetabar.h:17: error: parse error before `private'
kmetabar.h:21: error: destructors must be member functions
kmetabar.h:23: error: virtual outside class declaration
kmetabar.h: In function `QWidget* getWidget()':
kmetabar.h:23: error: `view' undeclared (first use this function)
kmetabar.h:23: error: (Each undeclared identifier is reported only once for
   each function it appears in.)
kmetabar.h: At global scope:
kmetabar.h:24: error: virtual outside class declaration
kmetabar.h:26: error: parse error before `protected'
kmetabar.h:28: error: `MetaScrollView*view' used prior to declaration
kmetabar.h:30: error: virtual outside class declaration
kmetabar.h:31: error: virtual outside class declaration
kmetabar.h:33: error: parse error before `}' token
In file included from kmetabar.cpp:6:
kmetabar.moc:23: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc:27: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc:27: error: assignment (not initialization) in declaration
kmetabar.moc:28: error: incomplete type `Metabar' does not have member `
   staticMetaObject'
kmetabar.moc:32: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc:40: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc:51: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc: In member function `QMetaObject* Metabar::staticMetaObject()':
kmetabar.moc:52: error: `metaObj' undeclared (first use this function)
kmetabar.moc:54: error: `KonqSidebarPlugin' undeclared (first use this
   function)
kmetabar.moc:54: error: parse error before `::' token
kmetabar.moc: At global scope:
kmetabar.moc:69: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc: In member function `void* Metabar::qt_cast(const char*)':
kmetabar.moc:72: error: parse error before `::' token
kmetabar.moc: At global scope:
kmetabar.moc:76: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc: In member function `bool Metabar::qt_invoke(int, QUObject*)':
kmetabar.moc:77: error: parse error before `::' token
kmetabar.moc:76: warning: unused parameter `int _id'
kmetabar.moc:76: warning: unused parameter `QUObject*_o'
kmetabar.moc: At global scope:
kmetabar.moc:81: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc: In member function `bool Metabar::qt_emit(int, QUObject*)':
kmetabar.moc:82: error: parse error before `::' token
kmetabar.moc:81: warning: unused parameter `int _id'
kmetabar.moc:81: warning: unused parameter `QUObject*_o'
kmetabar.moc: At global scope:
kmetabar.moc:87: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc: In member function `bool Metabar::qt_property(int, int,
   QVariant*)':
kmetabar.moc:88: error: parse error before `::' token
kmetabar.moc:87: warning: unused parameter `int id'
kmetabar.moc:87: warning: unused parameter `int f'
kmetabar.moc:87: warning: unused parameter `QVariant*v'
kmetabar.moc: At global scope:
kmetabar.moc:91: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.cpp:9: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.cpp: In constructor `Metabar::Metabar(KInstance*, QObject*, QWidget*,
   QString&, const char*)':
kmetabar.cpp:10: error: class `Metabar' does not have any field named `
   KonqSidebarPlugin'
kmetabar.cpp:12: error: `widget' undeclared (first use this function)
kmetabar.cpp: At global scope:
kmetabar.cpp:23: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.cpp:28: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.cpp:37: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.cpp: In function `void* create_konqsidebar_kmetabar(KInstance*,
   QObject*, QWidget*, QString&, const char*)':
kmetabar.cpp:60: error: parse error before `(' token
kmetabar.cpp:59: warning: unused parameter `KInstance*instance'
kmetabar.cpp:59: warning: unused parameter `QObject*par'
kmetabar.cpp:59: warning: unused parameter `QWidget*widp'
kmetabar.cpp:59: warning: unused parameter `QString&desktopname'
kmetabar.cpp:59: warning: unused parameter `const char*name'
/usr/include/kde/arts/core.h: At top level:
kmetabar.h:17: warning: `bool qt_static_property(QObject*, int, int, QVariant*)
   ' declared `static' but never defined
kmetabar.h:17: warning: `QMetaObject* staticMetaObject()' declared `static' but
   never defined
kmetabar.h:17: warning: `QString tr(const char*, const char*)' declared
   `static' but never defined
kmetabar.h:17: warning: `QString trUtf8(const char*, const char*)' declared
   `static' but never defined
make[2]: *** [kmetabar.lo] Error 1
make[2]: Leaving directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar'
make: *** [all] Error 2
-------------------[END of make errors]--------------------



I will put the "sudo checkinstall" errors too

-------------------[debut of sudo checkinstall error]---------------
"checkinstall 1.5.3, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Installing with "make install"...

============== Installation results =======================

Copying documentation directory...
Making install in doc
make[1]: Entering directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc'
Making install in .
make[2]: Entering directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc'
make[3]: Entering directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc'
make[2]: Leaving directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc'
Making install in en
make[2]: Entering directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc/en'
make[3]: Entering directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc/en'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../admin/mkinstalldirs /usr/share/doc/HTML/en/sidebar
/usr/bin/install -c -p -m 644 index.docbook /usr/share/doc/HTML/en/sidebar/index.docbook
/bin/sh ../../admin/mkinstalldirs /usr/share/doc/HTML/en/sidebar
/usr/bin/install -c -p -m 644 index.cache.bz2 /usr/share/doc/HTML/en/sidebar/
rm -f /usr/share/doc/HTML/en/sidebar/common
ln -s /usr/share/doc/kde/HTML/en/common /usr/share/doc/HTML/en/sidebar/common
make[3]: Leaving directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc/en'
make[2]: Leaving directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc/en'
make[1]: Leaving directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/doc'
Making install in po
make[1]: Entering directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/po'
make[2]: Entering directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/po'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/po'
make[1]: Leaving directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/po'
Making install in src
make[1]: Entering directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/src'
if /bin/sh ../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I/usr/X11R6/include  -I/usr/include/kde/arts   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT kmetabar.lo -MD -MP -MF ".deps/kmetabar.Tpo" -c -o kmetabar.lo kmetabar.cpp; \
then mv -f ".deps/kmetabar.Tpo" ".deps/kmetabar.Plo"; else rm -f ".deps/kmetabar.Tpo"; exit 1; fi
In file included from kmetabar.cpp:5:
kmetabar.h:8:31: konqsidebarplugin.h: No such file or directory
In file included from kmetabar.cpp:5:
kmetabar.h:16: error: parse error before `{' token
kmetabar.h:17: error: virtual outside class declaration
kmetabar.h:17: error: non-member function `const char* className()' cannot have
   `const' method qualifier
kmetabar.h:17: error: virtual outside class declaration
kmetabar.h:17: error: virtual outside class declaration
kmetabar.h:17: error: virtual outside class declaration
kmetabar.h:17: error: virtual outside class declaration
kmetabar.h: In function `QObject* qObject()':
kmetabar.h:17: error: invalid use of `this' in non-member function
kmetabar.h: At global scope:
kmetabar.h:17: error: parse error before `private'
kmetabar.h:21: error: destructors must be member functions
kmetabar.h:23: error: virtual outside class declaration
kmetabar.h: In function `QWidget* getWidget()':
kmetabar.h:23: error: `view' undeclared (first use this function)
kmetabar.h:23: error: (Each undeclared identifier is reported only once for
   each function it appears in.)
kmetabar.h: At global scope:
kmetabar.h:24: error: virtual outside class declaration
kmetabar.h:26: error: parse error before `protected'
kmetabar.h:28: error: `MetaScrollView*view' used prior to declaration
kmetabar.h:30: error: virtual outside class declaration
kmetabar.h:31: error: virtual outside class declaration
kmetabar.h:33: error: parse error before `}' token
In file included from kmetabar.cpp:6:
kmetabar.moc:23: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc:27: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc:27: error: assignment (not initialization) in declaration
kmetabar.moc:28: error: incomplete type `Metabar' does not have member `
   staticMetaObject'
kmetabar.moc:32: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc:40: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc:51: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc: In member function `QMetaObject* Metabar::staticMetaObject()':
kmetabar.moc:52: error: `metaObj' undeclared (first use this function)
kmetabar.moc:54: error: `KonqSidebarPlugin' undeclared (first use this
   function)
kmetabar.moc:54: error: parse error before `::' token
kmetabar.moc: At global scope:
kmetabar.moc:69: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc: In member function `void* Metabar::qt_cast(const char*)':
kmetabar.moc:72: error: parse error before `::' token
kmetabar.moc: At global scope:
kmetabar.moc:76: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc: In member function `bool Metabar::qt_invoke(int, QUObject*)':
kmetabar.moc:77: error: parse error before `::' token
kmetabar.moc:76: warning: unused parameter `int _id'
kmetabar.moc:76: warning: unused parameter `QUObject*_o'
kmetabar.moc: At global scope:
kmetabar.moc:81: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc: In member function `bool Metabar::qt_emit(int, QUObject*)':
kmetabar.moc:82: error: parse error before `::' token
kmetabar.moc:81: warning: unused parameter `int _id'
kmetabar.moc:81: warning: unused parameter `QUObject*_o'
kmetabar.moc: At global scope:
kmetabar.moc:87: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.moc: In member function `bool Metabar::qt_property(int, int,
   QVariant*)':
kmetabar.moc:88: error: parse error before `::' token
kmetabar.moc:87: warning: unused parameter `int id'
kmetabar.moc:87: warning: unused parameter `int f'
kmetabar.moc:87: warning: unused parameter `QVariant*v'
kmetabar.moc: At global scope:
kmetabar.moc:91: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.cpp:9: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.cpp: In constructor `Metabar::Metabar(KInstance*, QObject*, QWidget*,
   QString&, const char*)':
kmetabar.cpp:10: error: class `Metabar' does not have any field named `
   KonqSidebarPlugin'
kmetabar.cpp:12: error: `widget' undeclared (first use this function)
kmetabar.cpp: At global scope:
kmetabar.cpp:23: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.cpp:28: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.cpp:37: error: invalid use of undefined type `class Metabar'
kmetabar.h:15: error: forward declaration of `class Metabar'
kmetabar.cpp: In function `void* create_konqsidebar_kmetabar(KInstance*,
   QObject*, QWidget*, QString&, const char*)':
kmetabar.cpp:60: error: parse error before `(' token
kmetabar.cpp:59: warning: unused parameter `KInstance*instance'
kmetabar.cpp:59: warning: unused parameter `QObject*par'
kmetabar.cpp:59: warning: unused parameter `QWidget*widp'
kmetabar.cpp:59: warning: unused parameter `QString&desktopname'
kmetabar.cpp:59: warning: unused parameter `const char*name'
/usr/include/kde/arts/core.h: At top level:
kmetabar.h:17: warning: `bool qt_static_property(QObject*, int, int, QVariant*)
   ' declared `static' but never defined
kmetabar.h:17: warning: `QMetaObject* staticMetaObject()' declared `static' but
   never defined
kmetabar.h:17: warning: `QString tr(const char*, const char*)' declared
   `static' but never defined
kmetabar.h:17: warning: `QString trUtf8(const char*, const char*)' declared
   `static' but never defined
make[1]: *** [kmetabar.lo] Error 1
make[1]: Leaving directory `/home/username/Desktop/28725-kmetabar-0.2-beta2/kmetabar-0.2-beta2/kmetabar/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye."
-------------------[End of sudo checkinstall errors]---------------------

hope this what you asked for
Thanx

---

### Post by raven on 2005-10-07
when you asked me to post the errors
I start reading them line by line
and I discovered that I need kdebase-dev package
I downloaded it and all worked fine
thanx Knome_fan

---

