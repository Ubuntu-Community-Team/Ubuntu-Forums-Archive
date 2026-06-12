---
title: "amarok build help"
date: 2006-08-29
forum: Desktop Environments
---

### Post by Finsta on 2006-08-29
Hello all, on Xubuntu  here. I'm trying to build Amarok and it dies on make after a few seconds about some kde files missing and I cannot get ./configure to recognize the fact that I have libmp4v2 installed. What do you guys suggest?

Here's the error that it dies on when using make:

```
In file included from amarokdcophandler.cpp:32:
../../../amarok/src/htmlview.h:9:26: error: khtml_events.h: No such file or directory
../../../amarok/src/htmlview.h:10:24: error: khtml_part.h: No such file or directory
../../../amarok/src/htmlview.h:11:23: error: khtmlview.h: No such file or directory
../../../amarok/src/htmlview.h:16: error: expected class-name before '{' token
make[4]: *** [amarokdcophandler.lo] Error 1
make[4]: Leaving directory `/tmp/amarok-1.4.2/amarok/src/amarokcore'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/tmp/amarok-1.4.2/amarok/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/tmp/amarok-1.4.2/amarok'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/amarok-1.4.2'
make: *** [all] Error 2

```

---

### Post by croak77 on 2006-08-29
Can I ask why you want to compile amarok instead of using a deb?

---

### Post by Finsta on 2006-08-29
Well...for MP4/AAC as a first and iPod support

---

### Post by croak77 on 2006-08-29
Try this;

[http://kubuntu.org/announcements/amarok-1.4.1.php](http://kubuntu.org/announcements/amarok-1.4.1.php)

---

### Post by Finsta on 2006-08-29
Well just for the hell of it I want to build it, I'd rather not install a .deb

---

### Post by mlind on 2006-08-29
For that error, install package called **kdelibs4-dev**.

---

### Post by Finsta on 2006-08-29
I just installed it through Synaptic[kdelibs4], no luck.

---

### Post by croak77 on 2006-08-29
It's much easier to just use the .deb. First there might be patch's that are needed that aren't included with the amarok src. Second you'll have to enable options when you ./configue. Like ./configure  --prefix=/opt/kde --with-gnu-ld --enable-mysql --with-mp4v2 --with-ifp --with-libgpod --without-gstreamer --without-arts --with-xine and maybe more.

---

### Post by Finsta on 2006-08-29
I'm highly aware of the configure options. It just confuses me on how I cannot get it to compile.

---

### Post by croak77 on 2006-08-29
Well you should post the whole ./configure so we can see what options you enabled/disabled and what is missing or can't be found.

---

### Post by Finsta on 2006-08-29
./configure --without-arts --with-mp4v2 --disable-debug [I omitted --with-libgpod since it detected it automatically] --prefix=/usr/local/kde

That's it.
[Edit:I'll post the output in a second and I meant kde4libs-dev]

---

### Post by PriceChild on 2006-08-29
> **Finsta said:**
> I just installed it through Synaptic[kdelibs4], no luck.
mlind suggested kdelibs4-dev not kdelibs4

---

### Post by Finsta on 2006-08-29
```
finsta@Fruitloops:/tmp/amarok-1.4.2$ ./configure --without-arts --with-mp4v2 --disable-debug --prefix=/usr/local/kde
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/local/kde/bin/kde-config
checking where to install... /usr/local/kde (as requested)
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
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wno-non-virtual-dtor... yes
checking whether g++ supports -fno-reorder-blocks... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking whether system headers can cope with -O2 -fno-inline... irrelevant
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
checking for socklen_t... yes
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
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking for res_init... yes
checking if res_init needs custom prototype... no
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
checking for PIE support... yes
checking if enabling -pie/fPIE support... yes
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
checking for KDE... libraries /usr/local/kde/lib, headers /usr/local/kde/includechecking if UIC has KDE plugins available... yes
checking for KDE paths... defaults
checking for dcopidl... /usr/local/kde/bin/dcopidl
checking for dcopidl2cpp... /usr/local/kde/bin/dcopidl2cpp
checking for meinproc... /usr/local/kde/bin/meinproc
checking for kconfig_compiler... /usr/local/kde/bin/kconfig_compiler
checking for dcopidlng... /usr/local/kde/bin/dcopidlng
checking for makekdewidgets... /usr/bin/makekdewidgets
checking for xmllint... /usr/bin/xmllint
checking for Qt docs... NO
checking for dot... not found
checking for doxygen... not found
checking for pkg-config... yes
checking for taglib-config... /usr/local/bin/taglib-config
checking for ruby... /usr/bin/ruby
checking for xine-config... yes
checking for xine-lib version >= 1.0.2... yes
checking linux/inotify.h usability... yes
checking linux/inotify.h presence... yes
checking for linux/inotify.h... yes
checking for Qt with OpenGL support... yes
checking for int... (cached) yes
checking size of int... (cached) 4
checking for short... (cached) yes
checking size of short... (cached) 2
checking for long... (cached) yes
checking size of long... (cached) 4
checking for char *... (cached) yes
checking size of char *... (cached) 4
checking for xmms-config... no
checking for gtk-config... no
checking for sdl-config... yes
checking for pkg-config... /usr/bin/pkg-config
checking for libvisual-0.4 >= 0.4.0... checking tunepimp-0.5/tp_c.h usability... no
checking tunepimp-0.5/tp_c.h presence... no
checking for tunepimp-0.5/tp_c.h... no
checking tunepimp/tp_c.h usability... yes
checking tunepimp/tp_c.h presence... yes
checking for tunepimp/tp_c.h... yes
checking for tr_GetPUID in -ltunepimp... no
checking for tp_SetFileNameEncoding in -ltunepimp... no
checking if sched_setaffinity should be enabled... yes
checking konqsidebarplugin.h usability... no
checking konqsidebarplugin.h presence... no
checking for konqsidebarplugin.h... no
checking for _init in -lkonqsidebarplugin... no
checking for libnjb... checking for libmtp... checking ifp.h usability... no
checking ifp.h presence... no
checking for ifp.h... no
checking usb.h usability... no
checking usb.h presence... no
checking for usb.h... no

checking for libgpod-1.0... yes
checking LIBGPOD_CFLAGS... -I/usr/include/gpod-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking LIBGPOD_LIBS... -lgpod -lglib-2.0
checking for itdb_track_set_thumbnails... yes
checking for itdb_get_mountpoint... no
checking for itdb_device_get_ipod_info... no
checking for struct _Itdb_Track.movie_flag... no
checking for struct _Itdb_Track.skip_when_shuffling... no
checking for statvfs... yes
checking systems.h usability... yes
checking systems.h presence... yes
checking for systems.h... yes
checking for mp4.h... yes
checking for MP4Read in -lmp4v2... yes
checking if KDE is at least 3.4 for DAAP support... yes
checking /usr/lib/ruby/1.8/i486-linux... checking if amarok should be compiled... yes
checking if doc should be compiled... yes
checking if po should be compiled... yes
configure: creating ./config.status
fast creating Makefile
fast creating amarok/Makefile
fast creating amarok/src/Makefile
fast creating amarok/src/amarokcore/Makefile
fast creating amarok/src/analyzers/Makefile
fast creating amarok/src/collectionscanner/Makefile
fast creating amarok/src/data/Makefile
fast creating amarok/src/device/Makefile
fast creating amarok/src/device/massstorage/Makefile
fast creating amarok/src/device/nfs/Makefile
fast creating amarok/src/device/smb/Makefile
fast creating amarok/src/engine/Makefile
fast creating amarok/src/engine/akode/Makefile
fast creating amarok/src/engine/helix/Makefile
fast creating amarok/src/engine/helix/config/Makefile
fast creating amarok/src/engine/helix/helix-sp/Makefile
fast creating amarok/src/engine/kdemm/Makefile
fast creating amarok/src/engine/mas/Makefile
fast creating amarok/src/engine/nmm/Makefile
fast creating amarok/src/engine/nmm/icons/Makefile
fast creating amarok/src/engine/void/Makefile
fast creating amarok/src/engine/xine/Makefile
fast creating amarok/src/images/Makefile
fast creating amarok/src/images/icons/Makefile
fast creating amarok/src/konquisidebar/Makefile
fast creating amarok/src/loader/Makefile
fast creating amarok/src/mediadevice/Makefile
fast creating amarok/src/mediadevice/daap/Makefile
fast creating amarok/src/mediadevice/daap/daapreader/Makefile
fast creating amarok/src/mediadevice/daap/daapreader/authentication/Makefile
fast creating amarok/src/mediadevice/daap/mongrel/http11/Makefile
fast creating amarok/src/mediadevice/fs/Makefile
fast creating amarok/src/mediadevice/generic/Makefile
fast creating amarok/src/mediadevice/ifp/Makefile
fast creating amarok/src/mediadevice/ipod/Makefile
fast creating amarok/src/mediadevice/mtp/Makefile
fast creating amarok/src/mediadevice/njb/Makefile
fast creating amarok/src/metadata/Makefile
fast creating amarok/src/metadata/aac/Makefile
fast creating amarok/src/metadata/audible/Makefile
fast creating amarok/src/metadata/m4a/Makefile
fast creating amarok/src/metadata/mp4/Makefile
fast creating amarok/src/metadata/rmff/Makefile
fast creating amarok/src/metadata/wma/Makefile
fast creating amarok/src/plugin/Makefile
fast creating amarok/src/scripts/Makefile
fast creating amarok/src/scripts/common/Makefile
fast creating amarok/src/scripts/graphequalizer/Makefile
fast creating amarok/src/scripts/lyrics_astraweb/Makefile
fast creating amarok/src/scripts/lyrics_lyrc/Makefile
fast creating amarok/src/scripts/playlist2html/Makefile
fast creating amarok/src/scripts/ruby_debug/Makefile
fast creating amarok/src/scripts/score_default/Makefile
fast creating amarok/src/scripts/score_impulsive/Makefile
fast creating amarok/src/scripts/templates/Makefile
fast creating amarok/src/scripts/webcontrol/Makefile
fast creating amarok/src/sqlite/Makefile
fast creating amarok/src/statusbar/Makefile
fast creating amarok/src/themes/Makefile
fast creating amarok/src/themes/example/Makefile
fast creating amarok/src/themes/reinhardt/Makefile
fast creating amarok/src/themes/reinhardt/images/Makefile
fast creating amarok/src/vis/Makefile
fast creating amarok/src/vis/libvisual/Makefile
fast creating amarok/src/vis/xmmswrapper/Makefile
fast creating doc/Makefile
fast creating doc/amarok/Makefile
fast creating doc/da/Makefile
fast creating doc/de/Makefile
fast creating doc/es/Makefile
fast creating doc/et/Makefile
fast creating doc/fr/Makefile
fast creating doc/it/Makefile
fast creating doc/nl/Makefile
fast creating doc/pl/Makefile
fast creating doc/pt/Makefile
fast creating doc/pt_BR/Makefile
fast creating doc/ru/Makefile
fast creating doc/sv/Makefile
fast creating po/Makefile
fast creating po/af/Makefile
fast creating po/az/Makefile
fast creating po/bg/Makefile
fast creating po/br/Makefile
fast creating po/ca/Makefile
fast creating po/cs/Makefile
fast creating po/cy/Makefile
fast creating po/da/Makefile
fast creating po/de/Makefile
fast creating po/el/Makefile
fast creating po/en_GB/Makefile
fast creating po/es/Makefile
fast creating po/et/Makefile
fast creating po/fi/Makefile
fast creating po/fr/Makefile
fast creating po/ga/Makefile
fast creating po/gl/Makefile
fast creating po/he/Makefile
fast creating po/hi/Makefile
fast creating po/hu/Makefile
fast creating po/is/Makefile
fast creating po/it/Makefile
fast creating po/ja/Makefile
fast creating po/ka/Makefile
fast creating po/km/Makefile
fast creating po/ko/Makefile
fast creating po/lt/Makefile
fast creating po/ms/Makefile
fast creating po/nb/Makefile
fast creating po/nl/Makefile
fast creating po/nn/Makefile
fast creating po/pa/Makefile
fast creating po/pl/Makefile
fast creating po/pt/Makefile
fast creating po/pt_BR/Makefile
fast creating po/ro/Makefile
fast creating po/ru/Makefile
fast creating po/rw/Makefile
fast creating po/sl/Makefile
fast creating po/sr/Makefile
fast creating po/sr@Latn/Makefile
fast creating po/sv/Makefile
fast creating po/ta/Makefile
fast creating po/tg/Makefile
fast creating po/th/Makefile
fast creating po/tr/Makefile
fast creating po/uk/Makefile
fast creating po/uz/Makefile
fast creating po/zh_CN/Makefile
fast creating po/zh_TW/Makefile
config.pl: fast created 130 file(s).
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

 ==========================
 ===  Amarok - PLUGINS  ======================================================== ==========================
 =
 = The following extra functionality will NOT be included:
 =   - NMM-engine
 =   - Helix-engine
 =   - libvisual Support
 =   - XMMS Visualization Wrapper
 =   - MySql Support
 =   - Postgresql Support
 =   - Konqueror Sidebar
 =   - iRiver iFP Support
 =   - Creative Nomad Jukebox Support
 =   - MTP Device Support
 =
 = The following extra functionality will be included:
 =   + xine-engine
 =   + MusicBrainz Support
 =   + MP4/AAC Tag Write Support
 =   + iPod Support (with Artwork)
 =
 ===============================================================================

```
And yes, I installed kdelibs4-dev through Synaptic

---

### Post by croak77 on 2006-08-29
No idea. Maybe someone else can help.

---

### Post by mlind on 2006-08-29
> **croak77 said:**
> No idea. Maybe someone else can help.

What's the problem? That ouput looks normal now.

---

### Post by orb9220 on 2006-08-29
This installed 1.4.2 for me.

wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)

sudo -s

apt-key add kubuntu-packages-jriddell-key.gpg

echo "deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main" >> /etc/apt/sources.list

apt-get update

apt-get install amarok amarok-engines

---

### Post by Finsta on 2006-08-29
> **mlind said:**
> What's the problem? That ouput looks normal now.
Make dies in a few seconds.

---

### Post by croak77 on 2006-08-30
Is it a different make error then the one in your original post?

---

### Post by mlind on 2006-08-30
> **Finsta said:**
> Make dies in a few seconds.

Post the error then

---

### Post by Finsta on 2006-08-30
> **croak77 said:**
> Is it a different make error then the one in your original post?

Nope. It just dies after that.

---

### Post by mlind on 2006-08-30
> **Finsta said:**
> Nope. It just dies after that.

That's not very useful info if you don't post the output of what's actually happening..

---

