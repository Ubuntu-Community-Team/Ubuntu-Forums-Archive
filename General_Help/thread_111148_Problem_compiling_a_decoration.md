---
title: "Problem compiling a decoration"
date: 2006-01-01
forum: General Help
---

### Post by Neo Ex on 2006-01-01
Hi to all.
I tried to compile the [Plastik Classic]("http://www.kde-look.org/content/show.php?content=27731") window decoration: I have written ./configure in a terminal, and, at the end, it said 'Good - your configure finished. Start make now'.
But if I start make it give me an error:

```

daniel@d83-184-206-198:~/archivi/plastik-classic-0.1.0$ sudo make
Password:
make  all-recursive
make[1]: Entering directory `/home/daniel/archivi/plastik-classic-0.1.0'
Making all in config
make[2]: Entering directory `/home/daniel/archivi/plastik-classic-0.1.0/config'
cd . && /bin/sh /home/daniel/archivi/plastik-classic-0.1.0/admin/missing --run aclocal-1.6
cd .. && \
  /bin/sh /home/daniel/archivi/plastik-classic-0.1.0/admin/missing --run automake-1.6 --foreign  Makefile
cd .. && perl admin/am_edit plastik-0.1.0/Makefile.in
/bin/sh ./config.status --recheck
/bin/sh: ./config.status: No such file or directory
make[2]: *** [config.status] Error 127
make[2]: Leaving directory `/home/daniel/archivi/plastik-classic-0.1.0/config'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/daniel/archivi/plastik-classic-0.1.0'
make: *** [all] Error 2
daniel@d83-184-206-198:~/archivi/plastik-classic-0.1.0$

```

How can I solve?
Thank you.

---

### Post by alvonsius on 2006-01-01
try installing autoconf and automake1.6

---

### Post by Neo Ex on 2006-01-02
I already have autoconf and automake1.6.

---

### Post by Freddy on 2006-01-02
Don't use "sudo make".

Use:
```
./configure --prefix=`kde-config --prefix`
make
sudo make install
```
/// Freddan

---

### Post by Neo Ex on 2006-01-02
It gives me an error again:

```

daniel@d83-184-206-198:~/archivi/plastik-classic-0.1.0$ make
make  all-recursive
make[1]: Entering directory `/home/daniel/archivi/plastik-classic-0.1.0'
Making all in config
make[2]: Entering directory `/home/daniel/archivi/plastik-classic-0.1.0/config'
cd . && /bin/sh /home/daniel/archivi/plastik-classic-0.1.0/admin/missing --run aclocal-1.6
cd .. && \
  /bin/sh /home/daniel/archivi/plastik-classic-0.1.0/admin/missing --run automake-1.6 --foreign  Makefile
cd .. && perl admin/am_edit plastik-0.1.0/Makefile.in
/bin/sh ./config.status --recheck
/bin/sh: ./config.status: No such file or directory
make[2]: *** [config.status] Error 127
make[2]: Leaving directory `/home/daniel/archivi/plastik-classic-0.1.0/config'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/daniel/archivi/plastik-classic-0.1.0'
make: *** [all] Error 2
daniel@d83-184-206-198:~/archivi/plastik-classic-0.1.0$

```

---

### Post by Neo Ex on 2006-01-03
Nobody can help me...?

---

### Post by sharke on 2006-01-03
okay
to install the commands are
./install.sh
sudo make install
do notuse
./configure or make

Regards
Sharke

---

### Post by Neo Ex on 2006-01-03
It starts checking and configuring (twice), and it said 'Good - your configure finished. Start make now' (twice).
But when it starts to compile, it give me some error:

```

make  all-recursive
make[1]: Entering directory `/home/daniel/archivi/plastik-classic-0.1.0'
Making all in config
make[2]: Entering directory `/home/daniel/archivi/plastik-classic-0.1.0/config'
cd . && /bin/sh /home/daniel/archivi/plastik-classic-0.1.0/admin/missing --run aclocal-1.6
cd .. && \
  /bin/sh /home/daniel/archivi/plastik-classic-0.1.0/admin/missing --run automake-1.6 --foreign  Makefile
cd .. && perl admin/am_edit plastik-0.1.0/Makefile.in
make  all-am
make[3]: Entering directory `/home/daniel/archivi/plastik-classic-0.1.0/config'
cd . && /bin/sh /home/daniel/archivi/plastik-classic-0.1.0/admin/missing --run aclocal-1.6
cd .. && \
  /bin/sh /home/daniel/archivi/plastik-classic-0.1.0/admin/missing --run automake-1.6 --foreign  Makefile
cd .. && perl admin/am_edit plastik-0.1.0/Makefile.in
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload -o configdialog.h configdialog.ui
source='config.cpp' object='config.lo' libtool=yes \
depfile='.deps/config.Plo' tmpdepfile='.deps/config.TPlo' \
depmode=gcc3 /bin/sh ../admin/depcomp \
/bin/sh ./libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -c -o config.lo `test -f 'config.cpp' || echo './'`config.cpp
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
/usr/share/qt3/bin/moc configdialog.h -o configdialog.moc
rm -f configdialog.cpp
echo '#include <klocale.h>' > configdialog.cpp
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload -tr tr2i18n -i configdialog.h configdialog.ui > configdialog.cpp.temp ; ret=$?; \
sed -e "s,tr2i18n( \"\" ),QString::null,g" configdialog.cpp.temp | sed -e "s,tr2i18n( \"\"\, \"\" ),QString::null,g" | sed -e "s,image\([0-9][0-9]*\)_data,img\1_configdialog,g" >> configdialog.cpp ;\
rm -f configdialog.cpp.temp ;\
if test "$ret" = 0; then echo '#include "configdialog.moc"' >> configdialog.cpp; else rm -f configdialog.cpp ; exit $ret ; fi
source='configdialog.cpp' object='configdialog.lo' libtool=yes \
depfile='.deps/configdialog.Plo' tmpdepfile='.deps/configdialog.TPlo' \
depmode=gcc3 /bin/sh ../admin/depcomp \
/bin/sh ./libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -c -o configdialog.lo `test -f 'configdialog.cpp' || echo './'`configdialog.cpp
/usr/share/qt3/include/qtooltip.h:86: warning: 'class QToolTip' has virtual functions but non-virtual destructor
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
/bin/sh ./libtool --silent --mode=link --tag=CXX g++  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common    -o kwin_plastikclassic_config.la.closure kwin_plastikclassic_config_la_closure.lo -L/usr/X11R6/lib -L/usr/lib  -avoid-version -module -no-undefined  -R /usr/lib -R /usr/X11R6/lib  -module config.lo configdialog.lo -lkdeui
/bin/sh ./libtool --silent --mode=link --tag=CXX g++  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common    -o kwin_plastikclassic_config.la -rpath /lib/kde3 -L/usr/X11R6/lib -L/usr/lib  -avoid-version -module -no-undefined  -R /usr/lib -R /usr/X11R6/lib  -module config.lo configdialog.lo -lkdeui
make[3]: Leaving directory `/home/daniel/archivi/plastik-classic-0.1.0/config'
make[2]: Leaving directory `/home/daniel/archivi/plastik-classic-0.1.0/config'
make[2]: Entering directory `/home/daniel/archivi/plastik-classic-0.1.0'
cd . && /bin/sh ./config.status Makefile depfiles
config.status: creating Makefile
config.status: executing depfiles commands
make[2]: Leaving directory `/home/daniel/archivi/plastik-classic-0.1.0'
make[2]: Entering directory `/home/daniel/archivi/plastik-classic-0.1.0'
/usr/share/qt3/bin/moc ./plastik.h -o plastik.moc
source='plastik.cpp' object='plastik.lo' libtool=yes \
depfile='.deps/plastik.Plo' tmpdepfile='.deps/plastik.TPlo' \
depmode=gcc3 /bin/sh ./admin/depcomp \
/bin/sh ./libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I. -I./../../lib -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -DQT_PLUGIN -c -o plastik.lo `test -f 'plastik.cpp' || echo './'`plastik.cpp
In file included from plastik.cpp:26:
plastik.h:26:25: error: kdecoration.h: No such file or directory
plastik.h:27:32: error: kdecorationfactory.h: No such file or directory
plastik.h:60: error: expected class-name before '{' token
plastik.h:67: error: ISO C++ forbids declaration of 'KDecoration' with no type
plastik.h:67: error: 'KDecoration' declared as a 'virtual' field
plastik.h:67: error: expected ';' before '*' token
plastik.h:68: error: 'Ability' has not been declared
plastik.h:83: error: incomplete type 'KWinPlastik::PlastikHandler' used in nested name specifier
plastik.h:83: error: incomplete type 'KWinPlastik::PlastikHandler' used in nested name specifier
plastik.h:83: error: template argument 1 is invalid
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
plastik.moc: In member function 'virtual void* KWinPlastik::PlastikHandler::qt_cast(const char*)':
plastik.moc:73: error: 'KDecorationFactory' was not declared in this scope
plastik.moc:73: error: expected primary-expression before ')' token
plastik.moc:73: error: expected ';' before 'this'
plastik.moc:73: warning: statement has no effect
plastikclient.h: At global scope:
plastikclient.h:38: error: expected class-name before '{' token
plastikclient.h:41: error: expected `)' before '*' token
plastikclient.h:71: error: 'Position' does not name a type
plastikclient.h:38: warning: 'class KWinPlastik::PlastikClient' has virtual functions but non-virtual destructor
plastikclient.h: In member function 'QPixmap KWinPlastik::PlastikClient::getTitleBarTile(bool) const':
plastikclient.h:53: error: return type 'struct QPixmap' is incomplete
plastikclient.h:54: confused by earlier errors, bailing out
make[2]: *** [plastik.lo] Error 1
make[2]: Leaving directory `/home/daniel/archivi/plastik-classic-0.1.0'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/daniel/archivi/plastik-classic-0.1.0'
make: *** [all] Error 2
daniel@d83-184-206-198:~/archivi/plastik-classic-0.1.0$ 

```

---

### Post by Zeddicus on 2006-01-04
Are you sure you have the appropriate -dev packages installed?  I recall having a similar problem earlier, but fixed it after installing... some kde -dev packages.  (kdelibs4-dev, maybe?)

EDIT:  You're missing kdecoration.h -- install kdebase-dev and you should be fine. :)

---

### Post by GeneralZod on 2006-01-04
[QUOTE=Zeddicus]Are you sure you have the appropriate -dev packages installed? I recall having a similar problem earlier, but fixed it after installing... some kde -dev packages. (kdelibs4-dev, maybe?)[/QUOTE]

Close - it's actually "kdebase-dev" :)

Edit:

Doh - too late! :D

---

### Post by Neo Ex on 2006-01-04
I installed kdebase-dev, but it give me however this error:

```

make  all-recursive
make[1]: Entering directory `/home/daniel/archivi/plastik-classic-0.1.0'
Making all in config
make[2]: Entering directory `/home/daniel/archivi/plastik-classic-0.1.0/config'
cd . && /bin/sh /home/daniel/archivi/plastik-classic-0.1.0/admin/missing --run aclocal-1.6
cd .. && \
  /bin/sh /home/daniel/archivi/plastik-classic-0.1.0/admin/missing --run automake-1.6 --foreign  Makefile
cd .. && perl admin/am_edit plastik-0.1.0/Makefile.in
make  all-am
make[3]: Entering directory `/home/daniel/archivi/plastik-classic-0.1.0/config'
cd . && /bin/sh /home/daniel/archivi/plastik-classic-0.1.0/admin/missing --run aclocal-1.6
cd .. && \
  /bin/sh /home/daniel/archivi/plastik-classic-0.1.0/admin/missing --run automake-1.6 --foreign  Makefile
cd .. && perl admin/am_edit plastik-0.1.0/Makefile.in
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload -o configdialog.h configdialog.ui
source='config.cpp' object='config.lo' libtool=yes \
depfile='.deps/config.Plo' tmpdepfile='.deps/config.TPlo' \
depmode=gcc3 /bin/sh ../admin/depcomp \
/bin/sh ./libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -c -o config.lo `test -f 'config.cpp' || echo './'`config.cpp
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
/usr/share/qt3/bin/moc configdialog.h -o configdialog.moc
rm -f configdialog.cpp
echo '#include <klocale.h>' > configdialog.cpp
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload -tr tr2i18n -i configdialog.h configdialog.ui > configdialog.cpp.temp ; ret=$?; \
sed -e "s,tr2i18n( \"\" ),QString::null,g" configdialog.cpp.temp | sed -e "s,tr2i18n( \"\"\, \"\" ),QString::null,g" | sed -e "s,image\([0-9][0-9]*\)_data,img\1_configdialog,g" >> configdialog.cpp ;\
rm -f configdialog.cpp.temp ;\
if test "$ret" = 0; then echo '#include "configdialog.moc"' >> configdialog.cpp; else rm -f configdialog.cpp ; exit $ret ; fi
source='configdialog.cpp' object='configdialog.lo' libtool=yes \
depfile='.deps/configdialog.Plo' tmpdepfile='.deps/configdialog.TPlo' \
depmode=gcc3 /bin/sh ../admin/depcomp \
/bin/sh ./libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -c -o configdialog.lo `test -f 'configdialog.cpp' || echo './'`configdialog.cpp
/usr/share/qt3/include/qtooltip.h:86: warning: 'class QToolTip' has virtual functions but non-virtual destructor
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
/bin/sh ./libtool --silent --mode=link --tag=CXX g++  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common    -o kwin_plastikclassic_config.la.closure kwin_plastikclassic_config_la_closure.lo -L/usr/X11R6/lib -L/usr/lib  -avoid-version -module -no-undefined  -R /usr/lib -R /usr/X11R6/lib  -module config.lo configdialog.lo -lkdeui
/bin/sh ./libtool --silent --mode=link --tag=CXX g++  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common    -o kwin_plastikclassic_config.la -rpath /lib/kde3 -L/usr/X11R6/lib -L/usr/lib  -avoid-version -module -no-undefined  -R /usr/lib -R /usr/X11R6/lib  -module config.lo configdialog.lo -lkdeui
make[3]: Leaving directory `/home/daniel/archivi/plastik-classic-0.1.0/config'
make[2]: Leaving directory `/home/daniel/archivi/plastik-classic-0.1.0/config'
make[2]: Entering directory `/home/daniel/archivi/plastik-classic-0.1.0'
cd . && /bin/sh ./config.status Makefile depfiles
config.status: creating Makefile
config.status: executing depfiles commands
make[2]: Leaving directory `/home/daniel/archivi/plastik-classic-0.1.0'
make[2]: Entering directory `/home/daniel/archivi/plastik-classic-0.1.0'
/usr/share/qt3/bin/moc ./plastik.h -o plastik.moc
source='plastik.cpp' object='plastik.lo' libtool=yes \
depfile='.deps/plastik.Plo' tmpdepfile='.deps/plastik.TPlo' \
depmode=gcc3 /bin/sh ./admin/depcomp \
/bin/sh ./libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I. -I./../../lib -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -DQT_PLUGIN -c -o plastik.lo `test -f 'plastik.cpp' || echo './'`plastik.cpp
/usr/include/kde/kdecoration.h:176: warning: 'class KDecorationProvides' has virtual functions but non-virtual destructor
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
/usr/share/qt3/bin/moc ./plastikclient.h -o plastikclient.moc
source='plastikclient.cpp' object='plastikclient.lo' libtool=yes \
depfile='.deps/plastikclient.Plo' tmpdepfile='.deps/plastikclient.TPlo' \
depmode=gcc3 /bin/sh ./admin/depcomp \
/bin/sh ./libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I. -I./../../lib -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -DQT_PLUGIN -c -o plastikclient.lo `test -f 'plastikclient.cpp' || echo './'`plastikclient.cpp
/usr/include/kde/kdecoration.h:176: warning: 'class KDecorationProvides' has virtual functions but non-virtual destructor
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
/usr/share/qt3/bin/moc ./plastikbutton.h -o plastikbutton.moc
source='plastikbutton.cpp' object='plastikbutton.lo' libtool=yes \
depfile='.deps/plastikbutton.Plo' tmpdepfile='.deps/plastikbutton.TPlo' \
depmode=gcc3 /bin/sh ./admin/depcomp \
/bin/sh ./libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I. -I./../../lib -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -DQT_PLUGIN -c -o plastikbutton.lo `test -f 'plastikbutton.cpp' || echo './'`plastikbutton.cpp
/usr/share/qt3/include/qtooltip.h:86: warning: 'class QToolTip' has virtual functions but non-virtual destructor
/usr/include/kde/kdecoration.h:176: warning: 'class KDecorationProvides' has virtual functions but non-virtual destructor
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
source='misc.cpp' object='misc.lo' libtool=yes \
depfile='.deps/misc.Plo' tmpdepfile='.deps/misc.TPlo' \
depmode=gcc3 /bin/sh ./admin/depcomp \
/bin/sh ./libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I. -I./../../lib -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -DQT_PLUGIN -c -o misc.lo `test -f 'misc.cpp' || echo './'`misc.cpp
source='shadow.cpp' object='shadow.lo' libtool=yes \
depfile='.deps/shadow.Plo' tmpdepfile='.deps/shadow.TPlo' \
depmode=gcc3 /bin/sh ./admin/depcomp \
/bin/sh ./libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I. -I./../../lib -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -pedantic -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -DQT_PLUGIN -c -o shadow.lo `test -f 'shadow.cpp' || echo './'`shadow.cpp
make[2]: *** No rule to make target `/lib/libkdecorations.la', needed by `kwin3_plastikclassic.la.closure'.  Stop.
make[2]: Leaving directory `/home/daniel/archivi/plastik-classic-0.1.0'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/daniel/archivi/plastik-classic-0.1.0'
make: *** [all] Error 2
daniel@d83-184-206-198:~/archivi/plastik-classic-0.1.0$

```

---

### Post by Kujen on 2007-01-12
Oh come on, I finally find a topic with the same problem I'm having and there was never a solution? Can nobody install kde decoration themes or what? :p

---

