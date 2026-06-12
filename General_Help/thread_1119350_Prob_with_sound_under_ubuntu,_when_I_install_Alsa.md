---
title: "Prob with sound under ubuntu, when I install Alsa"
date: 2009-04-07
forum: General Help
---

### Post by Mimoo_Tz on 2009-04-07
hi , ..; 
I have some problems when I'm compiling lib Alsa , I dont know these the missage


==================================
7018/sndop-mixer.alisp'
test -z "/usr/share/alsa/cards" || mkdir -p -- "/usr/share/alsa/cards"
 /usr/bin/install -c -m 644 'aliases.conf' '/usr/share/alsa/cards/aliases.conf'
 /usr/bin/install -c -m 644 'AACI.conf' '/usr/share/alsa/cards/AACI.conf'
 /usr/bin/install -c -m 644 'ATIIXP.conf' '/usr/share/alsa/cards/ATIIXP.conf'
 /usr/bin/install -c -m 644 'ATIIXP-SPDMA.conf' '/usr/share/alsa/cards/ATIIXP-SPDMA.conf'
 /usr/bin/install -c -m 644 'ATIIXP-MODEM.conf' '/usr/share/alsa/cards/ATIIXP-MODEM.conf'
 /usr/bin/install -c -m 644 'AU8810.conf' '/usr/share/alsa/cards/AU8810.conf'
 /usr/bin/install -c -m 644 'AU8820.conf' '/usr/share/alsa/cards/AU8820.conf'
 /usr/bin/install -c -m 644 'AU8830.conf' '/usr/share/alsa/cards/AU8830.conf'
 /usr/bin/install -c -m 644 'Audigy.conf' '/usr/share/alsa/cards/Audigy.conf'
 /usr/bin/install -c -m 644 'Audigy2.conf' '/usr/share/alsa/cards/Audigy2.conf'
 /usr/bin/install -c -m 644 'Aureon51.conf' '/usr/share/alsa/cards/Aureon51.conf'
 /usr/bin/install -c -m 644 'Aureon71.conf' '/usr/share/alsa/cards/Aureon71.conf'
 /usr/bin/install -c -m 644 'CA0106.conf' '/usr/share/alsa/cards/CA0106.conf'
 /usr/bin/install -c -m 644 'CMI8338.conf' '/usr/share/alsa/cards/CMI8338.conf'
 /usr/bin/install -c -m 644 'CMI8338-SWIEC.conf' '/usr/share/alsa/cards/CMI8338-SWIEC.conf'
 /usr/bin/install -c -m 644 'CMI8738-MC6.conf' '/usr/share/alsa/cards/CMI8738-MC6.conf'
 /usr/bin/install -c -m 644 'CMI8738-MC8.conf' '/usr/share/alsa/cards/CMI8738-MC8.conf'
 /usr/bin/install -c -m 644 'CMI8788.conf' '/usr/share/alsa/cards/CMI8788.conf'
 /usr/bin/install -c -m 644 'CS46xx.conf' '/usr/share/alsa/cards/CS46xx.conf'
 /usr/bin/install -c -m 644 'EMU10K1.conf' '/usr/share/alsa/cards/EMU10K1.conf'
 /usr/bin/install -c -m 644 'EMU10K1X.conf' '/usr/share/alsa/cards/EMU10K1X.conf'
 /usr/bin/install -c -m 644 'ENS1370.conf' '/usr/share/alsa/cards/ENS1370.conf'
 /usr/bin/install -c -m 644 'ENS1371.conf' '/usr/share/alsa/cards/ENS1371.conf'
 /usr/bin/install -c -m 644 'ES1968.conf' '/usr/share/alsa/cards/ES1968.conf'
 /usr/bin/install -c -m 644 'FM801.conf' '/usr/share/alsa/cards/FM801.conf'
 /usr/bin/install -c -m 644 'GUS.conf' '/usr/share/alsa/cards/GUS.conf'
 /usr/bin/install -c -m 644 'HDA-Intel.conf' '/usr/share/alsa/cards/HDA-Intel.conf'
 /usr/bin/install -c -m 644 'ICE1712.conf' '/usr/share/alsa/cards/ICE1712.conf'
 /usr/bin/install -c -m 644 'ICE1724.conf' '/usr/share/alsa/cards/ICE1724.conf'
 /usr/bin/install -c -m 644 'ICH.conf' '/usr/share/alsa/cards/ICH.conf'
 /usr/bin/install -c -m 644 'ICH4.conf' '/usr/share/alsa/cards/ICH4.conf'
 /usr/bin/install -c -m 644 'ICH-MODEM.conf' '/usr/share/alsa/cards/ICH-MODEM.conf'
 /usr/bin/install -c -m 644 'Maestro3.conf' '/usr/share/alsa/cards/Maestro3.conf'
 /usr/bin/install -c -m 644 'NFORCE.conf' '/usr/share/alsa/cards/NFORCE.conf'
 /usr/bin/install -c -m 644 'PC-Speaker.conf' '/usr/share/alsa/cards/PC-Speaker.conf'
 /usr/bin/install -c -m 644 'PMac.conf' '/usr/share/alsa/cards/PMac.conf'
 /usr/bin/install -c -m 644 'PMacToonie.conf' '/usr/share/alsa/cards/PMacToonie.conf'
 /usr/bin/install -c -m 644 'PS3.conf' '/usr/share/alsa/cards/PS3.conf'
 /usr/bin/install -c -m 644 'RME9636.conf' '/usr/share/alsa/cards/RME9636.conf'
 /usr/bin/install -c -m 644 'RME9652.conf' '/usr/share/alsa/cards/RME9652.conf'
 /usr/bin/install -c -m 644 'SI7018.conf' '/usr/share/alsa/cards/SI7018.conf'
 /usr/bin/install -c -m 644 'TRID4DWAVENX.conf' '/usr/share/alsa/cards/TRID4DWAVENX.conf'
 /usr/bin/install -c -m 644 'USB-Audio.conf' '/usr/share/alsa/cards/USB-Audio.conf'
 /usr/bin/install -c -m 644 'YMF744.conf' '/usr/share/alsa/cards/YMF744.conf'
 /usr/bin/install -c -m 644 'VIA686A.conf' '/usr/share/alsa/cards/VIA686A.conf'
 /usr/bin/install -c -m 644 'VIA8233.conf' '/usr/share/alsa/cards/VIA8233.conf'
 /usr/bin/install -c -m 644 'VIA8233A.conf' '/usr/share/alsa/cards/VIA8233A.conf'
 /usr/bin/install -c -m 644 'VIA8237.conf' '/usr/share/alsa/cards/VIA8237.conf'
 /usr/bin/install -c -m 644 'VX222.conf' '/usr/share/alsa/cards/VX222.conf'
 /usr/bin/install -c -m 644 'VXPocket.conf' '/usr/share/alsa/cards/VXPocket.conf'
 /usr/bin/install -c -m 644 'VXPocket440.conf' '/usr/share/alsa/cards/VXPocket440.conf'
 /usr/bin/install -c -m 644 'aliases.alisp' '/usr/share/alsa/cards/aliases.alisp'
make[4]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src/conf/cards'
make[3]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src/conf/cards'
Making install in pcm
make[3]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src/conf/pcm'
make[4]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src/conf/pcm'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/alsa/pcm" || mkdir -p -- "/usr/share/alsa/pcm"
 /usr/bin/install -c -m 644 'default.conf' '/usr/share/alsa/pcm/default.conf'
 /usr/bin/install -c -m 644 'front.conf' '/usr/share/alsa/pcm/front.conf'
 /usr/bin/install -c -m 644 'rear.conf' '/usr/share/alsa/pcm/rear.conf'
 /usr/bin/install -c -m 644 'center_lfe.conf' '/usr/share/alsa/pcm/center_lfe.conf'
 /usr/bin/install -c -m 644 'side.conf' '/usr/share/alsa/pcm/side.conf'
 /usr/bin/install -c -m 644 'surround40.conf' '/usr/share/alsa/pcm/surround40.conf'
 /usr/bin/install -c -m 644 'surround41.conf' '/usr/share/alsa/pcm/surround41.conf'
 /usr/bin/install -c -m 644 'surround50.conf' '/usr/share/alsa/pcm/surround50.conf'
 /usr/bin/install -c -m 644 'surround51.conf' '/usr/share/alsa/pcm/surround51.conf'
 /usr/bin/install -c -m 644 'surround71.conf' '/usr/share/alsa/pcm/surround71.conf'
 /usr/bin/install -c -m 644 'iec958.conf' '/usr/share/alsa/pcm/iec958.conf'
 /usr/bin/install -c -m 644 'hdmi.conf' '/usr/share/alsa/pcm/hdmi.conf'
 /usr/bin/install -c -m 644 'modem.conf' '/usr/share/alsa/pcm/modem.conf'
 /usr/bin/install -c -m 644 'dmix.conf' '/usr/share/alsa/pcm/dmix.conf'
 /usr/bin/install -c -m 644 'dsnoop.conf' '/usr/share/alsa/pcm/dsnoop.conf'
 /usr/bin/install -c -m 644 'dpl.conf' '/usr/share/alsa/pcm/dpl.conf'
make[4]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src/conf/pcm'
make[3]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src/conf/pcm'
make[3]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src/conf'
make[4]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src/conf'
make[4]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/alsa" || mkdir -p -- "/usr/share/alsa"
 /usr/bin/install -c -m 644 'alsa.conf' '/usr/share/alsa/alsa.conf'
 /usr/bin/install -c -m 644 'sndo-mixer.alisp' '/usr/share/alsa/sndo-mixer.alisp'
 /usr/bin/install -c -m 644 'smixer.conf' '/usr/share/alsa/smixer.conf'
make[4]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src/conf'
make[3]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src/conf'
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src/conf'
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src'
make[3]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libasound.la' '/usr/lib/libasound.la'
/usr/bin/install -c .libs/libasound.so.2.0.0 /usr/lib/libasound.so.2.0.0
(cd /usr/lib && { ln -s -f libasound.so.2.0.0 libasound.so.2 || { rm -f libasound.so.2 && ln -s libasound.so.2.0.0 libasound.so.2; }; })
(cd /usr/lib && { ln -s -f libasound.so.2.0.0 libasound.so || { rm -f libasound.so && ln -s libasound.so.2.0.0 libasound.so; }; })
/usr/bin/install -c .libs/libasound.lai /usr/lib/libasound.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src'
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src'
make[1]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/src'
Making install in modules
make[1]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules'
Making install in mixer
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules/mixer'
Making install in simple
make[3]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules/mixer/simple'
make[4]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules/mixer/simple'
test -z "/usr/lib/alsa-lib/smixer" || mkdir -p -- "/usr/lib/alsa-lib/smixer"
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'smixer-sbase.la' '/usr/lib/alsa-lib/smixer/smixer-sbase.la'
libtool: install: warning: relinking `smixer-sbase.la'
(cd /usr/src/alsa/Alsas/alsa-lib-1.0.19/modules/mixer/simple; /bin/bash ../../../libtool  --tag=CC --mode=relink gcc -g -O2 -W -Wall -g -O2 -o smixer-sbase.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version sbase.lo ../../../src/libasound.la )
gcc -shared  .libs/sbase.o  -L/usr/lib -lasound  -Wl,-soname -Wl,smixer-sbase.so -o .libs/smixer-sbase.so
/usr/bin/install -c .libs/smixer-sbase.soT /usr/lib/alsa-lib/smixer/smixer-sbase.so
/usr/bin/install -c .libs/smixer-sbase.lai /usr/lib/alsa-lib/smixer/smixer-sbase.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/alsa-lib/smixer
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/alsa-lib/smixer

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'smixer-ac97.la' '/usr/lib/alsa-lib/smixer/smixer-ac97.la'
libtool: install: warning: relinking `smixer-ac97.la'
(cd /usr/src/alsa/Alsas/alsa-lib-1.0.19/modules/mixer/simple; /bin/bash ../../../libtool  --tag=CC --mode=relink gcc -g -O2 -W -Wall -g -O2 -o smixer-ac97.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version ac97.lo sbasedl.lo ../../../src/libasound.la )
gcc -shared  .libs/ac97.o .libs/sbasedl.o  -L/usr/lib -lasound  -Wl,-soname -Wl,smixer-ac97.so -o .libs/smixer-ac97.so
/usr/bin/install -c .libs/smixer-ac97.soT /usr/lib/alsa-lib/smixer/smixer-ac97.so
/usr/bin/install -c .libs/smixer-ac97.lai /usr/lib/alsa-lib/smixer/smixer-ac97.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/alsa-lib/smixer
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/alsa-lib/smixer

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/bash ../../../libtool --mode=install /usr/bin/install -c  'smixer-hda.la' '/usr/lib/alsa-lib/smixer/smixer-hda.la'
libtool: install: warning: relinking `smixer-hda.la'
(cd /usr/src/alsa/Alsas/alsa-lib-1.0.19/modules/mixer/simple; /bin/bash ../../../libtool  --tag=CC --mode=relink gcc -g -O2 -W -Wall -g -O2 -o smixer-hda.la -rpath /usr/lib/alsa-lib/smixer -module -avoid-version hda.lo sbasedl.lo ../../../src/libasound.la )
gcc -shared  .libs/hda.o .libs/sbasedl.o  -L/usr/lib -lasound  -Wl,-soname -Wl,smixer-hda.so -o .libs/smixer-hda.so
/usr/bin/install -c .libs/smixer-hda.soT /usr/lib/alsa-lib/smixer/smixer-hda.so
/usr/bin/install -c .libs/smixer-hda.lai /usr/lib/alsa-lib/smixer/smixer-hda.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/alsa-lib/smixer
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/alsa-lib/smixer

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules/mixer/simple'
make[3]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules/mixer/simple'
make[3]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules/mixer'
make[4]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules/mixer'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules/mixer'
make[3]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules/mixer'
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules/mixer'
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules'
make[3]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules'
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules'
make[1]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/modules'
Making install in aserver
make[1]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/aserver'
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/aserver'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'aserver' '/usr/bin/aserver'
/usr/bin/install -c .libs/aserver /usr/bin/aserver
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/aserver'
make[1]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/aserver'
Making install in alsalisp
make[1]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/alsalisp'
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/alsalisp'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/alsalisp'
make[1]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/alsalisp'
Making install in test
make[1]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/test'
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/test'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/test'
make[1]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/test'
Making install in utils
make[1]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/utils'
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/utils'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/aclocal" || mkdir -p -- "/usr/share/aclocal"
 /usr/bin/install -c -m 644 'alsa.m4' '/usr/share/aclocal/alsa.m4'
test -z "/usr/lib/pkgconfig" || mkdir -p -- "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 'alsa.pc' '/usr/lib/pkgconfig/alsa.pc'
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/utils'
make[1]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19/utils'
make[1]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19'
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19'
make[1]: Leaving directory `/usr/src/alsa/Alsas/alsa-lib-1.0.19'
mimoo@MiMoO-Laptop:/usr/src/alsa/Alsas/alsa-lib-1.0.19$ cd ..
mimoo@MiMoO-Laptop:/usr/src/alsa/Alsas$ cd alsa-utils-*
mimoo@MiMoO-Laptop:/usr/src/alsa/Alsas/alsa-utils-1.0.19$ 
mimoo@MiMoO-Laptop:/usr/src/alsa/Alsas/alsa-utils-1.0.19$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.16... found.
checking for snd_ctl_open in -lasound... yes
checking for xmlto... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for ncurses5-config... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating alsactl/Makefile
config.status: creating alsactl/init/Makefile
config.status: creating alsamixer/Makefile
config.status: creating amidi/Makefile
config.status: creating amixer/Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating alsaconf/alsaconf
config.status: creating alsaconf/Makefile
config.status: creating alsaconf/po/Makefile
config.status: WARNING:  alsaconf/po/Makefile.in seems to ignore the --datarootdir setting
config.status: creating aplay/Makefile
config.status: creating include/Makefile
config.status: creating iecset/Makefile
config.status: creating utils/Makefile
config.status: creating utils/alsa-utils.spec
config.status: creating seq/Makefile
config.status: creating seq/aconnect/Makefile
config.status: creating seq/aplaymidi/Makefile
config.status: creating seq/aseqdump/Makefile
config.status: creating seq/aseqnet/Makefile
config.status: creating speaker-test/Makefile
config.status: creating speaker-test/samples/Makefile
config.status: creating include/aconfig.h
config.status: include/aconfig.h is unchanged
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing depfiles commands
mimoo@MiMoO-Laptop:/usr/src/alsa/Alsas/alsa-utils-1.0.19$ sudo make
Making all in include
make[1]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/include'
make  all-am
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/include'
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/include'
make[1]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/include'
Making all in alsactl
make[1]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl'
Making all in init
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl/init'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl/init'
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
	then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
alsactl.c: In function ‘main’:
alsactl.c:166: warning: assignment from incompatible pointer type
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \
	then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT utils.o -MD -MP -MF ".deps/utils.Tpo" -c -o utils.o utils.c; \
	then mv -f ".deps/utils.Tpo" ".deps/utils.Po"; else rm -f ".deps/utils.Tpo"; exit 1; fi
utils.c: In function ‘initfailed’:
utils.c:92: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
utils.c:93: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
utils.c:94: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
utils.c:95: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT init_parse.o -MD -MP -MF ".deps/init_parse.Tpo" -c -o init_parse.o init_parse.c; \
	then mv -f ".deps/init_parse.Tpo" ".deps/init_parse.Po"; else rm -f ".deps/init_parse.Tpo"; exit 1; fi
init_parse.c: In function ‘parse_line’:
init_parse.c:1550: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
init_parse.c:1560: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
gcc  -g -O2   -o alsactl  alsactl.o state.o utils.o init_parse.o  -lasound -lm -ldl -lpthread
xmlto man alsactl_init.xml
/bin/bash: xmlto: command not found
make[2]: *** [alsactl_init.7] Error 127
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl'
make: *** [all-recursive] Error 1
mimoo@MiMoO-Laptop:/usr/src/alsa/Alsas/alsa-utils-1.0.19$ sudo make
Making all in include
make[1]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/include'
make  all-am
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/include'
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/include'
make[1]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/include'
Making all in alsactl
make[1]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl'
Making all in init
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl/init'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl/init'
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl'
xmlto man alsactl_init.xml
/bin/bash: xmlto: command not found
make[2]: *** [alsactl_init.7] Error 127
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl'
make: *** [all-recursive] Error 1
mimoo@MiMoO-Laptop:/usr/src/alsa/Alsas/alsa-utils-1.0.19$ sudo make install
Making install in include
make[1]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/include'
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/include'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/include'
make[1]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/include'
Making install in alsactl
make[1]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl'
Making install in init
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl/init'
make[3]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl/init'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/alsa/init" || mkdir -p -- "/usr/share/alsa/init"
 /usr/bin/install -c -m 644 '00main' '/usr/share/alsa/init/00main'
 /usr/bin/install -c -m 644 'default' '/usr/share/alsa/init/default'
 /usr/bin/install -c -m 644 'help' '/usr/share/alsa/init/help'
 /usr/bin/install -c -m 644 'info' '/usr/share/alsa/init/info'
 /usr/bin/install -c -m 644 'test' '/usr/share/alsa/init/test'
 /usr/bin/install -c -m 644 'hda' '/usr/share/alsa/init/hda'
make[3]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl/init'
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl/init'
make[2]: Entering directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl'
xmlto man alsactl_init.xml
/bin/bash: xmlto: command not found
make[2]: *** [alsactl_init.7] Error 127
make[2]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/src/alsa/Alsas/alsa-utils-1.0.19/alsactl'
make: *** [install-recursive] Error 1
============================================================

---

