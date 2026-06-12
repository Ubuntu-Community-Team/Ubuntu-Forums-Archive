---
title: "errors with make"
date: 2005-12-16
forum: General Help
---

### Post by Slyder0244 on 2005-12-16
i can't seem to get make to finish i always get errors here are 2 examples

```
cd . && /bin/sh ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: Entering directory `/home/slyder/kompose-0.5.4'
Making all in doc
make[2]: Entering directory `/home/slyder/kompose-0.5.4/doc'
make[3]: Entering directory `/home/slyder/kompose-0.5.4/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/slyder/kompose-0.5.4/doc'
make[2]: Leaving directory `/home/slyder/kompose-0.5.4/doc'
Making all in po
make[2]: Entering directory `/home/slyder/kompose-0.5.4/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/slyder/kompose-0.5.4/po'
Making all in src
make[2]: Entering directory `/home/slyder/kompose-0.5.4/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.  -I `imlib2-config --cflags`  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -MT kompose.o -MD -MP -MF ".deps/kompose.Tpo" -c -o kompose.o kompose.cpp; \
then mv -f ".deps/kompose.Tpo" ".deps/kompose.Po"; else rm -f ".deps/kompose.Tpo"; exit 1; fi
/bin/sh: imlib2-config: command not found
kompose.cpp:88:23: error: kompose.moc: No such file or directory
/usr/share/qt3/include/qptrlist.h: In member function ‘void QPtrList<type>::deleteItem(void*) [with type = KomposeTask]’:
kompose.cpp:84:   instantiated from here
/usr/share/qt3/include/qptrlist.h:150: warning: possible problem detected in invocation of delete operator:
/usr/share/qt3/include/qptrlist.h:150: warning: invalid use of undefined type ‘struct KomposeTask’
komposetaskmanager.h:29: warning: forward declaration of ‘struct KomposeTask’
/usr/share/qt3/include/qptrlist.h:150: note: neither the destructor nor the class-specific operator delete will be called, even if they are declared when the class is defined.
make[2]: *** [kompose.o] Error 1
make[2]: Leaving directory `/home/slyder/kompose-0.5.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/slyder/kompose-0.5.4'
make: *** [all] Error 2
```

and here is the other example 

```
make  all-recursive
make[1]: Entering directory `/home/slyder/apollon-1.0.2.1'
Making all in apollon
make[2]: Entering directory `/home/slyder/apollon-1.0.2.1/apollon'
Making all in images
make[3]: Entering directory `/home/slyder/apollon-1.0.2.1/apollon/images'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/slyder/apollon-1.0.2.1/apollon/images'
Making all in libapollon
make[3]: Entering directory `/home/slyder/apollon-1.0.2.1/apollon/libapollon'
make[4]: Entering directory `/home/slyder/apollon-1.0.2.1/apollon/libapollon'
if /bin/sh ../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT libapollon.lo -MD -MP -MF ".deps/libapollon.Tpo" -c -o libapollon.lo libapollon.cpp; \
then mv -f ".deps/libapollon.Tpo" ".deps/libapollon.Plo"; else rm -f ".deps/libapollon.Tpo"; exit 1; fi
if /bin/sh ../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT giftsocket.lo -MD -MP -MF ".deps/giftsocket.Tpo" -c -o giftsocket.lo giftsocket.cpp; \
then mv -f ".deps/giftsocket.Tpo" ".deps/giftsocket.Plo"; else rm -f ".deps/giftsocket.Tpo"; exit 1; fi
if /bin/sh ../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT giftparse.lo -MD -MP -MF ".deps/giftparse.Tpo" -c -o giftparse.lo giftparse.cpp; \
then mv -f ".deps/giftparse.Tpo" ".deps/giftparse.Plo"; else rm -f ".deps/giftparse.Tpo"; exit 1; fi
/usr/share/qt3/bin/moc ./libapollon.h -o libapollon.moc.cpp
if /bin/sh ../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT libapollon.moc.lo -MD -MP -MF ".deps/libapollon.moc.Tpo" -c -o libapollon.moc.lo libapollon.moc.cpp; \
then mv -f ".deps/libapollon.moc.Tpo" ".deps/libapollon.moc.Plo"; else rm -f ".deps/libapollon.moc.Tpo"; exit 1; fi
/usr/share/qt3/include/private/qucom_p.h:69: warning: 'struct QUBuffer' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:77: warning: 'struct QUType' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:104: warning: 'struct QUType_Null' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:287: warning: 'struct QUType_enum' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:307: warning: 'struct QUType_ptr' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:326: warning: 'struct QUType_iface' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:345: warning: 'struct QUType_idisp' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:364: warning: 'struct QUType_bool' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:383: warning: 'struct QUType_int' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:403: warning: 'struct QUType_double' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:423: warning: 'struct QUType_charstar' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:444: warning: 'struct QUType_QString' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:65: warning: 'struct QUType_QVariant' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:87: warning: 'struct QUType_varptr' has virtual functions but non-virtual destructor
/usr/share/qt3/bin/moc ./giftsocket.h -o giftsocket.moc.cpp
if /bin/sh ../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT giftsocket.moc.lo -MD -MP -MF ".deps/giftsocket.moc.Tpo" -c -o giftsocket.moc.lo giftsocket.moc.cpp; \
then mv -f ".deps/giftsocket.moc.Tpo" ".deps/giftsocket.moc.Plo"; else rm -f ".deps/giftsocket.moc.Tpo"; exit 1; fi
/usr/share/qt3/include/private/qucom_p.h:69: warning: 'struct QUBuffer' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:77: warning: 'struct QUType' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:104: warning: 'struct QUType_Null' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:287: warning: 'struct QUType_enum' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:307: warning: 'struct QUType_ptr' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:326: warning: 'struct QUType_iface' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:345: warning: 'struct QUType_idisp' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:364: warning: 'struct QUType_bool' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:383: warning: 'struct QUType_int' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:403: warning: 'struct QUType_double' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:423: warning: 'struct QUType_charstar' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:444: warning: 'struct QUType_QString' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:65: warning: 'struct QUType_QVariant' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:87: warning: 'struct QUType_varptr' has virtual functions but non-virtual destructor
/bin/sh ../../libtool --silent --tag=CXX --mode=link g++  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common    -o libapollon.la -rpath /usr/local/kde/lib -L/usr/X11R6/lib -L/usr/share/qt3/lib -L/usr/lib  -R /usr/lib -R /usr/share/qt3/lib -R /usr/X11R6/lib -version-info 0:1:0 libapollon.lo giftsocket.lo giftparse.lo libapollon.moc.lo giftsocket.moc.lo  -lkdecore -lqt-mt  -lz -lpng -lz -lm -lXext -lX11  -lSM -lICE -lpthread
make[4]: Leaving directory `/home/slyder/apollon-1.0.2.1/apollon/libapollon'
make[3]: Leaving directory `/home/slyder/apollon-1.0.2.1/apollon/libapollon'
Making all in libkirc
make[3]: Entering directory `/home/slyder/apollon-1.0.2.1/apollon/libkirc'
/usr/share/qt3/bin/moc ./dcchandler.h -o dcchandler.moc
if /bin/sh ../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I/usr/include/kde -I/usr/share/qt3/include -I.  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT dcchandler.lo -MD -MP -MF ".deps/dcchandler.Tpo" -c -o dcchandler.lo dcchandler.cpp; \
then mv -f ".deps/dcchandler.Tpo" ".deps/dcchandler.Plo"; else rm -f ".deps/dcchandler.Tpo"; exit 1; fi
/usr/share/qt3/include/private/qucom_p.h:69: warning: 'struct QUBuffer' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:77: warning: 'struct QUType' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:104: warning: 'struct QUType_Null' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:287: warning: 'struct QUType_enum' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:307: warning: 'struct QUType_ptr' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:326: warning: 'struct QUType_iface' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:345: warning: 'struct QUType_idisp' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:364: warning: 'struct QUType_bool' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:383: warning: 'struct QUType_int' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:403: warning: 'struct QUType_double' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:423: warning: 'struct QUType_charstar' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:444: warning: 'struct QUType_QString' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:65: warning: 'struct QUType_QVariant' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:87: warning: 'struct QUType_varptr' has virtual functions but non-virtual destructor
/usr/share/qt3/bin/moc ./kirc.h -o kirc.moc
if /bin/sh ../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I/usr/include/kde -I/usr/share/qt3/include -I.  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT kirc.lo -MD -MP -MF ".deps/kirc.Tpo" -c -o kirc.lo kirc.cpp; \
then mv -f ".deps/kirc.Tpo" ".deps/kirc.Plo"; else rm -f ".deps/kirc.Tpo"; exit 1; fi
kirc.cpp:1115: warning: unused parameter 'msg'
kirc.cpp:1120: warning: unused parameter 'msg'
kirc.cpp:1254: warning: unused parameter 'msg'
kirc.cpp:1260: warning: unused parameter 'msg'
kirc.cpp:1625: warning: unused parameter 'msg'
/usr/share/qt3/include/private/qucom_p.h:69: warning: 'struct QUBuffer' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:77: warning: 'struct QUType' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:104: warning: 'struct QUType_Null' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:287: warning: 'struct QUType_enum' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:307: warning: 'struct QUType_ptr' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:326: warning: 'struct QUType_iface' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:345: warning: 'struct QUType_idisp' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:364: warning: 'struct QUType_bool' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:383: warning: 'struct QUType_int' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:403: warning: 'struct QUType_double' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:423: warning: 'struct QUType_charstar' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:444: warning: 'struct QUType_QString' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:65: warning: 'struct QUType_QVariant' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:87: warning: 'struct QUType_varptr' has virtual functions but non-virtual destructor
if /bin/sh ../../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I/usr/include/kde -I/usr/share/qt3/include -I.  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT kircmessage.lo -MD -MP -MF ".deps/kircmessage.Tpo" -c -o kircmessage.lo kircmessage.cpp; \
then mv -f ".deps/kircmessage.Tpo" ".deps/kircmessage.Plo"; else rm -f ".deps/kircmessage.Tpo"; exit 1; fi
/bin/sh ../../libtool --silent --tag=CXX --mode=link g++  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common    -o libkirc.la  -no-undefined -Wl,--no-undefined -Wl,--allow-shlib-undefined -avoid-version -module -no-undefined -Wl,--no-undefined -Wl,--allow-shlib-undefined -R /usr/lib -R /usr/share/qt3/lib -R /usr/X11R6/lib  dcchandler.lo kirc.lo kircmessage.lo -L/usr/X11R6/lib -L/usr/share/qt3/lib -L/usr/lib  -R /usr/lib -R /usr/share/qt3/lib -R /usr/X11R6/lib -lkio
grep: /lib/libacl.la: No such file or directory
/bin/sed: can't read /lib/libacl.la: No such file or directory
libtool: link: `/lib/libacl.la' is not a valid libtool archive
make[3]: *** [libkirc.la] Error 1
make[3]: Leaving directory `/home/slyder/apollon-1.0.2.1/apollon/libkirc'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/slyder/apollon-1.0.2.1/apollon'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/slyder/apollon-1.0.2.1'
make: *** [all] Error 2

```

and yes i know the 2 apps i've chosen for my example i can get in the repositories but i'd still like to be able to compile things from source and these are the 2 apps i've tried ./configure goes fine on both and i only have problems when coming to the make process 

also i have build-essential, gcc 3.4, and gcc 3.3

---

### Post by Peter76 on 2005-12-16
Hello, as far as I can see from your output, in the first it's saying imlib2-config is missing or cannot be found. Try if you can locate it and pass it to configure, or install it WITH the dev files.
The second one is complaining about libacl.la not being there.... Don't know this .la thing, but if you have a libacl.so on your system, try making a symbolic link from it to libacl.la....
Anyway (you probably know this ), always look at the first error you get to sort out your problems.
All the warnings you got in the second one don't matter a lot of times, ignore them.
good luck

---

### Post by GoldBuggie on 2005-12-16
first one should be **libimlib2-dev**.

second one is **libacl1-dev**

---

### Post by Slyder0244 on 2005-12-16
wow thanks for the quick reply guys i have both of those packages installed but i guess it's just not finding them although i did find the files by searching their actually both in usr/lib/ 

but anyways i know there is a way to link to them so that it'll know where they are although i'm still new to linux and don't know how so i'd really appreciate it if you guys could let me know the commands to do so

also i was wondering why it didn't find the files, like are they in the wrong place or does this just happen from time to time on linux 

anyways thanx again your help was great appreciated

---

### Post by Peter76 on 2005-12-16
Did you install those packages after make failed, or already before that? If after, you need to "make clean" and after that "./configure" again. Also you might check if pkgconfig is installed, this program is often used for finding libraries. Also check your configure output again, there might be something there which gives you a clue, although it wasn't fatal. Try ./configure --help for some possible options for showing where libraries are. Good luck

---

### Post by GoldBuggie on 2005-12-16
When compiling and such it is not always about having those files. I've had the exact same problem numerous of times and it all boild down to that it needs the header files that is the -dev package. But even before having the -dev package you will have the files but the make won't have every info on where to find and use them etc etec

---

### Post by Slyder0244 on 2005-12-16
thanks peter i can't remember if i installed them before or after i've been doing this for 2 days now but i tried make clean and ran it again and got the same error and then did make clean again and then linked to the libraries (or i'm pretty sure i did) because i didn't get the error about imlib2 anymore but i'm still getting some errors here are the make errors> make  all-recursive
make[1]: Entering directory `/home/slyder/kompose-0.5.4'
Making all in doc
make[2]: Entering directory `/home/slyder/kompose-0.5.4/doc'
make[3]: Entering directory `/home/slyder/kompose-0.5.4/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/slyder/kompose-0.5.4/doc'
make[2]: Leaving directory `/home/slyder/kompose-0.5.4/doc'
Making all in po
make[2]: Entering directory `/home/slyder/kompose-0.5.4/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/slyder/kompose-0.5.4/po'
Making all in src
make[2]: Entering directory `/home/slyder/kompose-0.5.4/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.  -I/usr/lib/ -I `imlib2-config --cflags`  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.cpp; \
then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.  -I/usr/lib/ -I `imlib2-config --cflags`  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -MT kompose.o -MD -MP -MF ".deps/kompose.Tpo" -c -o kompose.o kompose.cpp; \
then mv -f ".deps/kompose.Tpo" ".deps/kompose.Po"; else rm -f ".deps/kompose.Tpo"; exit 1; fi
kompose.cpp:88:23: error: kompose.moc: No such file or directory
/usr/share/qt3/include/qptrlist.h: In member function &#8216;void QPtrList<type>::deleteItem(void*) [with type = KomposeTask]&#8217;:
kompose.cpp:84:   instantiated from here
/usr/share/qt3/include/qptrlist.h:150: warning: possible problem detected in invocation of delete operator:
/usr/share/qt3/include/qptrlist.h:150: warning: invalid use of undefined type &#8216;struct KomposeTask&#8217;
komposetaskmanager.h:29: warning: forward declaration of &#8216;struct KomposeTask&#8217;
/usr/share/qt3/include/qptrlist.h:150: note: neither the destructor nor the class-specific operator delete will be called, even if they are declared when the class is defined.
make[2]: *** [kompose.o] Error 1
make[2]: Leaving directory `/home/slyder/kompose-0.5.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/slyder/kompose-0.5.4'
make: *** [all] Error 2


---

### Post by Slyder0244 on 2005-12-16
yea everywhere i read it always said to get the -dev files so i've gotten them for all the packages i thought i needed

---

### Post by Peter76 on 2005-12-16
Seems to me there now is a problem with the Qt toolkit. Check if you need a specific version of qt to compile.... See the README and or INSTALL files in the source directory or check the website of the program. Good luck again, and let me know if you sort it out.

---

### Post by GoldBuggie on 2005-12-16
When checking what kompose needs for packages
I saw it needed 

libimlib2-dev libltdl3-dev libungif4-dev libxmuu-dev libxpm-dev libxtrap-dev libxtst-dev x11proto-record-dev x11proto-trap-dev xlibs-dev

you can try and install them if you haven't. But the moc file creating error is a bit strange

---

### Post by Slyder0244 on 2005-12-16
yea well with kompose i went to the website and didn't find much helpful info there at least not for my problem but just for kicks i downloaded the previous source and tried to compile that and it worked just fine so maybe the problem wasn't on my end but i can't be for sure but i give up on the latest version i'm just happy i got it compiled

and for apollon i tried it again and ran into another error but this time i knew a little bit more about the errors (thanks to this thread) so i found the file it was missing and installed the -dev files and tried again and it compiled without a problem

so yay i compiled both of these apps which is exactly what i was wanting to do and thanks to all of you for your patience and help

now for a real dumb question once i get it compiled what do i do i see with kompose i have an executable and i don't have one for apollon but it's got a shell script do i just make short cuts to the shell script and executable or what

---

### Post by Peter76 on 2005-12-16
See what the shell script does.... And do a " make install "

---

