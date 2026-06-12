---
title: "Need help getting Kpilot to cmake"
date: 2007-02-13
forum: Desktop Environments
---

### Post by barney_1 on 2007-02-13
Hi Folks,

I've been trying to compile kpilot from source because the version in the repo doesn't sync changes made to my calendar in Kontact back to my palm pilot.  I'm having problems with cmake:

```
mike@krusty:~/kpilot$ make -f Makefile.cmake
test -d "build-Linux2_6_20_6_generic" || mkdir -p "build-Linux2_6_20_6_generic"
test -d "build-Linux2_6_20_6_generic"
SRC_DIR=`pwd` ; cd "build-Linux2_6_20_6_generic" && cmake $SRC_DIR
-- Found KDE3 include dir: /usr/include/kde
-- Found KDE3 library dir: /usr/lib
-- Found KDE3 dcopidl preprocessor: /usr/bin/dcopidl
-- Found KDE3 dcopidl2cpp preprocessor: /usr/bin/dcopidl2cpp
-- Found KDE3 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found pi-dlp.h in /usr/local/include
-- Found libpisock in /usr/local/lib/libpisock.so
-- Found pilot-link: /usr/local/lib/libpisock.so
-- Found libmal.h in /usr/include/libmal
-- Found libmal in /usr/lib/libmal.so
-- Found mal: /usr/lib/libmal.so
-- icon: /home/mike/kpilot/kpilot/Icons/mini-kpilot.png doesn't fit naming conventions. ignoring.
-- icon: /home/mike/kpilot/kpilot/Icons/busysync.png doesn't fit naming conventions. ignoring.
-- icon: /home/mike/kpilot/kpilot/Icons/fastsync.png doesn't fit naming conventions. ignoring.
-- icon: /home/mike/kpilot/kpilot/Icons/nosync.png doesn't fit naming conventions. ignoring.
-- icon: /home/mike/kpilot/kpilot/Icons/hotsync.png doesn't fit naming conventions. ignoring.
-- icon: /home/mike/kpilot/kpilot/Icons/kpilot-splash.png doesn't fit naming conventions. ignoring.
-- Although mal was found, the malconduit will not be compiled since it is unmaintained
-- BUILD: Normal build selected.
-- Configuring done
-- Generating done
-- Build files have been written to: /home/mike/kpilot/build-Linux2_6_20_6_generic
make[1]: Entering directory `/home/mike/kpilot/build-Linux2_6_20_6_generic'
make[2]: Entering directory `/home/mike/kpilot/build-Linux2_6_20_6_generic'
make[3]: Entering directory `/home/mike/kpilot/build-Linux2_6_20_6_generic'
[  1%] Building CXX object lib/CMakeFiles/kpilot.dir/pilotMemo.o
/home/mike/kpilot/lib/pilotMemo.h:101: error: could not convert template argument ‘unpack_MemoAppInfo’ to ‘int (*)(MemoAppInfo*, unsigned char*, unsigned int)’
/home/mike/kpilot/lib/pilotMemo.h:101: error: could not convert template argument ‘pack_MemoAppInfo’ to ‘int (*)(MemoAppInfo*, unsigned char*, unsigned int)’
/home/mike/kpilot/lib/pilotMemo.h:101: error: invalid type in declaration before ‘;’ token
make[3]: *** [lib/CMakeFiles/kpilot.dir/pilotMemo.o] Error 1
make[3]: Leaving directory `/home/mike/kpilot/build-Linux2_6_20_6_generic'
make[2]: *** [lib/CMakeFiles/kpilot.dir/all] Error 2
make[2]: Leaving directory `/home/mike/kpilot/build-Linux2_6_20_6_generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/mike/kpilot/build-Linux2_6_20_6_generic'
make: *** [all] Error 2

```

I'm running Feisty.  Can anyone help?

---

