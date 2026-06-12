---
title: "kaffeine svn build problems"
date: 2006-08-31
forum: Desktop Environments
---

### Post by mtron on 2006-08-31
cheers! I'm trying ti compile the latest kaffeine from svn Revision 579249. I'm on ubuntu 6.06 with the usual bild tools.

The configure runs good but when i run make it complains that "kaffeine_export.h" doesn't exist.

Did sb. come across this problem? 

Thanks

```
mtron@workstation:~/work/kaffeine/multimedia$ make
make  all-recursive
...
Making all in kaffeine
make[2]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine'
Making all in src
make[3]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src'
Making all in player-parts
make[4]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/player-parts'
Making all in .
make[5]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/player-parts'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/player-parts'
Making all in xine-part
make[5]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/player-parts/xine-part'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/player-parts/xine-part'
Making all in gstreamer-part
make[5]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/player-parts/gstreamer-part'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/player-parts/gstreamer-part'
make[4]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/player-parts'
Making all in input
make[4]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input'
Making all in .
make[5]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input'
Making all in dvbclient
make[5]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvbclient'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvbclient'
Making all in audiobrowser
make[5]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/audiobrowser'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/audiobrowser'Making all in disc
make[5]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/disc'
Making all in plugins
make[6]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/disc/plugins'
Making all in .
make[7]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/disc/plugins'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/disc/plugins'Making all in oggvorbis
make[7]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/disc/plugins/oggvorbis'
make[7]: Nothing to be done for `all'.
make[7]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/disc/plugins/oggvorbis'
Making all in mp3lame
make[7]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/disc/plugins/mp3lame'
make[7]: Nothing to be done for `all'.
make[7]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/disc/plugins/mp3lame'
make[6]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/disc/plugins'Making all in .
make[6]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/disc'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/disc'
make[5]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/disc'
Making all in dvb
make[5]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb'
Making all in lib
make[6]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib'
Making all in libdvbapi
make[7]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib/libdvbapi'
make[7]: Nothing to be done for `all'.
make[7]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib/libdvbapi'
Making all in libdvben50221
make[7]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib/libdvben50221'
make[7]: Nothing to be done for `all'.
make[7]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib/libdvben50221'
Making all in libucsi
make[7]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib/libucsi'
Making all in dvb
make[8]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib/libucsi/dvb'
make[8]: Nothing to be done for `all'.
make[8]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib/libucsi/dvb'
Making all in mpeg
make[8]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib/libucsi/mpeg'
make[8]: Nothing to be done for `all'.
make[8]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib/libucsi/mpeg'
Making all in .
make[8]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib/libucsi'
make[8]: Nothing to be done for `all-am'.
make[8]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib/libucsi'
make[7]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib/libucsi'
make[7]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib'
make[7]: Nothing to be done for `all-am'.
make[7]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib'
make[6]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/lib'
Making all in plugins
make[6]: Entering directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/plugins'if /bin/sh ../../../../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../../../../.. -I../../../../../kaffeine/src/input/dvb -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION  -MT kaffeinedvbplugin.lo -MD -MP -MF ".deps/kaffeinedvbplugin.Tpo" -c -o kaffeinedvbplugin.lo kaffeinedvbplugin.cpp; \
        then mv -f ".deps/kaffeinedvbplugin.Tpo" ".deps/kaffeinedvbplugin.Plo"; else rm -f ".deps/kaffeinedvbplugin.Tpo"; exit 1; fi
[B]In file included from kaffeinedvbplugin.cpp:23:
kaffeinedvbplugin.h:34:29: error: kaffeine_export.h: No such file or directory
kaffeinedvbplugin.h:40: error: invalid function declaration[/B]
kaffeinedvbplugin.moc:22: error: 'KaffeineDvbPlugin' has not been declared
kaffeinedvbplugin.moc:22: error: non-member function 'const char* className()' cannot have cv-qualifier
kaffeinedvbplugin.moc:27: error: 'KaffeineDvbPlugin' has not been declared
kaffeinedvbplugin.moc:28: error: 'KaffeineDvbPlugin' has not been declared
kaffeinedvbplugin.moc:28: error: 'staticMetaObject' was not declared in this scope
kaffeinedvbplugin.moc:50: error: 'KaffeineDvbPlugin' has not been declared
kaffeinedvbplugin.moc:72: error: 'KaffeineDvbPlugin' has not been declared
kaffeinedvbplugin.moc: In function 'void* qt_cast(const char*)':
kaffeinedvbplugin.moc:75: error: invalid use of 'this' in non-member function
kaffeinedvbplugin.moc:76: error: 'Part' has not been declared
kaffeinedvbplugin.moc: At global scope:
kaffeinedvbplugin.moc:79: error: 'KaffeineDvbPlugin' has not been declared
kaffeinedvbplugin.moc: In function 'bool qt_invoke(int, QUObject*)':
kaffeinedvbplugin.moc:82: error: 'configDialog' was not declared in this scope
kaffeinedvbplugin.moc:84: error: 'Part' has not been declared
kaffeinedvbplugin.moc: At global scope:
kaffeinedvbplugin.moc:89: error: 'KaffeineDvbPlugin' has not been declared
kaffeinedvbplugin.moc: In function 'bool qt_emit(int, QUObject*)':
kaffeinedvbplugin.moc:91: error: 'Part' has not been declared
kaffeinedvbplugin.moc: At global scope:
kaffeinedvbplugin.moc:95: error: 'KaffeineDvbPlugin' has not been declared
kaffeinedvbplugin.moc: In function 'bool qt_property(int, int, QVariant*)':
kaffeinedvbplugin.moc:97: error: 'Part' has not been declared
kaffeinedvbplugin.moc: At global scope:
kaffeinedvbplugin.moc:100: error: 'KaffeineDvbPlugin' has not been declared
kaffeinedvbplugin.cpp:28: error: 'KaffeineDvbPlugin' has not been declared
kaffeinedvbplugin.cpp:28: error: ISO C++ forbids declaration of 'KaffeineDvbPlugin' with no type
kaffeinedvbplugin.cpp: In function 'int KaffeineDvbPlugin(QObject*, const char*)':
kaffeinedvbplugin.cpp:28: error: only constructors take base initializers
kaffeinedvbplugin.cpp: At global scope:
kaffeinedvbplugin.cpp:34: error: expected constructor, destructor, or type conversion before '::' token
kaffeinedvbplugin.cpp: In function 'int KaffeineDvbPlugin(QObject*, const char*)':
kaffeinedvbplugin.cpp:30: warning: control reaches end of non-void function
make[6]: *** [kaffeinedvbplugin.lo] Error 1
make[6]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb/plugins'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input/dvb'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src/input'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mtron/work/kaffeine/multimedia/kaffeine'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mtron/work/kaffeine/multimedia'
make: *** [all] Error 2

```

---

### Post by mtron on 2006-09-11
symlinked kaffeine_export.h (in the directory kaffeine/src/) to kaffeine/src/input/dvb/plugins/

and it works. :D

---

