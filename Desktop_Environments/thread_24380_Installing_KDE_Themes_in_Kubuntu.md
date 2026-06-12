---
title: "Installing KDE Themes in Kubuntu"
date: 2005-04-06
forum: Desktop Environments
---

### Post by jagercola on 2005-04-06
Ok, I'm a first time linux / Kubuntu user and have learned alot just reading online.  The one thing which is the bane of my existance is getting themes from kde-look.org to install in Kubuntu.  They all come in source code format without a file to import directly into the theme manger in the control center.  So reading the various theme's instructions, they say do the classic compile method of ./configure, sudo make, and sudo make install.  I've done this for like 10 themes and none of them show up in the Theme Manager under Control Center.  The ./configure doesn't give any errors as I've installed a lot of various packages to make sure I can compile stuff.  Any help or advice?  Thanks!  -Will

Edit: I've also tried using "./configure --prefix=`/path/to/this/program/kde-config --prefix`" and changing "/path/to/this" to different directories.

---

### Post by apokryphos on 2005-04-07
You shouldn't be doing "sudo make" -- make should just be done with your permissions; only sudo make install will require root permissions, likely. You should be specifying the prefix of your KDEDIR when compiling a theme. On Ubuntu it's /usr (unless you compiled KDE), so:

./configure --prefix=/usr
make
sudo make install

---

### Post by getaceres on 2005-04-07
They don't appear in the theme manager. Look in the style section and they should be there.
Most of the themes you are downloading are styles. A theme is a style+windows decoration+icons+wallpaper+colors and so on. Normally you download and install those things separatelly and then apply some of them one by one.

---

### Post by jagercola on 2005-04-07
Here is what that configure command set to /usr outputs.  See anything wrong?

[QUOTE=jagercola]jagercola@Penguin:~/Desktop/dotcurve-1.0b3/dotcurve-1.0b3$ ./configure --prefix=
/usr
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as requested)
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
checking whether gcc supports -Wmissing-format-attribute... yes
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
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
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
checking for meinproc... /usr/bin/meinproc
checking for kconfig_compiler... /usr/bin/kconfig_compiler
checking for dcopidlng... /usr/bin/dcopidlng
checking for xmllint... /usr/bin/xmllint
checking if dotcurve should be compiled... yes
checking if dotcurve-3.2.90 should be compiled... no
configure: creating ./config.status
Can't open perl script "admin/conf.change.pl": No such file or directory
mv: cannot stat `./config.status.bak': No such file or directory
config.status: creating Makefile
config.status: creating dotcurve/Makefile
config.status: creating dotcurve/config/Makefile
config.status: creating config.h
config.status: executing depfiles commands

Good - your configure finished. Start make now
[/QUOTE]

---

### Post by jagercola on 2005-04-07
Also, here is the end of the output from sudo make install.

You guys see any glaring errors?  Thanks! -Will 

[QUOTE=jagercola]jagercola@Penguin:~/Desktop/dotcurve-1.0b3/dotcurve-1.0b3$ sudo make install
Password:
Making install in dotcurve
make[1]: Entering directory `/home/jagercola/Desktop/dotcurve-1.0b3/dotcurve-1.0b3/dotcurve'
Making install in config
make[2]: Entering directory `/home/jagercola/Desktop/dotcurve-1.0b3/dotcurve-1.0b3/dotcurve/config'
make[3]: Entering directory `/home/jagercola/Desktop/dotcurve-1.0b3/dotcurve-1.0b3/dotcurve/config'
/bin/sh ../../admin/mkinstalldirs /usr/lib/kde3
 /bin/sh ../../libtool --silent --mode=install /usr/bin/install -c -p  kstyle_dotcurve_config.la /usr/lib/kde3/kstyle_dotcurve_config.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kde3
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/jagercola/Desktop/dotcurve-1.0b3/dotcurve-1.0b3/dotcurve/config'
make[2]: Leaving directory `/home/jagercola/Desktop/dotcurve-1.0b3/dotcurve-1.0b3/dotcurve/config'
make[2]: Entering directory `/home/jagercola/Desktop/dotcurve-1.0b3/dotcurve-1.0b3/dotcurve'
make[3]: Entering directory `/home/jagercola/Desktop/dotcurve-1.0b3/dotcurve-1.0b3/dotcurve'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../admin/mkinstalldirs /usr/lib/kde3/plugins/styles
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c -p  dotcurve.la /usr/lib/kde3/plugins/styles/dotcurve.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kde3/plugins/styles
/bin/sh ../admin/mkinstalldirs /usr/share/apps/kstyle/themes
 /usr/bin/install -c -p -m 644 dotcurve.themerc /usr/share/apps/kstyle/themes/dotcurve.themerc
make[3]: Leaving directory `/home/jagercola/Desktop/dotcurve-1.0b3/dotcurve-1.0b3/dotcurve'
make[2]: Leaving directory `/home/jagercola/Desktop/dotcurve-1.0b3/dotcurve-1.0b3/dotcurve'
make[1]: Leaving directory `/home/jagercola/Desktop/dotcurve-1.0b3/dotcurve-1.0b3/dotcurve'
make[1]: Entering directory `/home/jagercola/Desktop/dotcurve-1.0b3/dotcurve-1.0b3'
make[2]: Entering directory `/home/jagercola/Desktop/dotcurve-1.0b3/dotcurve-1.0b3'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/jagercola/Desktop/dotcurve-1.0b3/dotcurve-1.0b3'
make[1]: Leaving directory `/home/jagercola/Desktop/dotcurve-1.0b3/dotcurve-1.0b3'
jagercola@Penguin:~/Desktop/dotcurve-1.0b3/dotcurve-1.0b3$   [/QUOTE]

---

### Post by getaceres on 2005-04-07
[QUOTE=jagercola]Here is what that configure command set to /usr outputs.  See anything wrong?[/QUOTE]
 I said you before. DotCurve is a style, is not a theme. It won't appear in the theme manager but in the styles section.

---

### Post by jagercola on 2005-04-07
[QUOTE=getaceres]I said you before. DotCurve is a style, is not a theme. It won't appear in the theme manager but in the styles section.[/QUOTE]
 
OMG! You are brillant!  Thanks for helping me learn!  I can't wait till I get to the level to give back to the kubuntu knowledge pool.

---

### Post by Ciddan on 2005-04-16
I keep getting this annoying error right at the end of the compile... I've tried different likley directories such as /usr and /usr/lib/kde3/ but it still gives me this error.. Any ideas on why? I'm new to Linux so any help would be appriceated!

[i]
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
[/i]

---

### Post by getaceres on 2005-04-16
[QUOTE=Ciddan]I keep getting this annoying error right at the end of the compile... I've tried different likley directories such as /usr and /usr/lib/kde3/ but it still gives me this error.. Any ideas on why? I'm new to Linux so any help would be appriceated!

[i]
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
[/i][/QUOTE]

You need to install kdebase-dev package to be able to compile themes.
To do this: 'sudo apt-get install kdebase-dev' or better using synaptic ;)

---

### Post by Ciddan on 2005-04-16
[QUOTE=getaceres]You need to install kdebase-dev package to be able to compile themes.
To do this: 'sudo apt-get install kdebase-dev' or better using synaptic ;)[/QUOTE]
 Aaah... Okay. Gonna try that now. Hope it works ;) Thanks

---

### Post by rowck001 on 2006-06-15
What if you just want to add a new window decorator.
I have downloaded decorator files (native KDE3.2+) that are just a collection of images and a ???.theme file.
Trying to add the files via theme manager wont work (as it is not a full theme I guess!?) but there seems to be no way to add them to the window decorator dialog.

Is there a specific folder these images need to go into? As I am using KDE 3.5 are these older (3.2) files incompatible?

---

### Post by peibol on 2006-09-01
Hi there, to install deKorator themes you have a specific panel. You've to go to System Preferences -> Appearance -> Window Decorations (select deKorator) and then you will find a tab named "Themes" with an "Install new theme" button at the bottom.

Hope this helps.

---

### Post by espmartin on 2007-08-02
Sorry for being such a noob, but...is there a program like Windowblinds for MS Win - made for linux? It seems that would be TONS easier to use for a noob
like me!

---

