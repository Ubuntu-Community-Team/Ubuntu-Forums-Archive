---
title: "kxmame for sdlmame compiling..."
date: 2008-03-02
forum: Gaming &amp; Leisure
---

### Post by Moonfrost on 2008-03-02
I was trying to compile kxmame CVS (which supports sdlmame) and I can't even configure the thing even though I have the ./configure files and and the make file but it tells me I don't have it...well here's an output if I input ./configure

```
./configure: No such file or directory
```

Then I read in the READ ME file that for this version (CVS version) I would have to input ```
make -f Makefile.cvs
```

and this is the output that I get

```

This Makefile is only for the CVS repository
This will be deleted before making the distribution

./admin/cvs.sh: 653: --version: not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
```

The I tried ```
apt-get install autoconf
```
which worked and it installed version 2.61-4

Then I tried the input ```
make -f Makefile.cvs
```

and I got this output again
```

 This Makefile is only for the CVS repository
This will be deleted before making the distribution

./admin/cvs.sh: 653: --version: not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
```

Then I tried ./configure again and it still tells me 

```
./configure: No such file or directory
```

---

### Post by Perfect Storm on 2008-03-03
```
sudo aptitude install autoconf automake autotools-dev pkg-config
```

Now you're equiped for the task.

---

### Post by Moonfrost on 2008-03-03
> **Artificial Intelligence said:**
> ```
sudo aptitude install autoconf automake autotools-dev pkg-config
```

Now you're equiped for the task.

Thanks a lot, I also had to install a newer version of automake or so it told me but everything worked and I was able to configure it...

the problem I'm having now is that it won't let me "make" or "make install" it tells me there's no make or make install files even though I can see them on the folder right there...am I done? or are there more commands that are different than the usual?

EDIT: Nevermind! all of a sudden now ./configure is working now so thanks a lot for your help!

EDIT: Well, I tried using ./configure and everything worked perfectly and it says I was good to go and input "make" but that showed this
```

user@userPC:~/Desktop/kxmame/trunk$ make
make  all-recursive
make[1]: Entering directory `/home/gedg/Desktop/kxmame/trunk'
Making all in doc
make[2]: Entering directory `/home/gedg/Desktop/kxmame/trunk/doc'
Making all in .
make[3]: Entering directory `/home/gedg/Desktop/kxmame/trunk/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/doc'
Making all in en
make[3]: Entering directory `/home/gedg/Desktop/kxmame/trunk/doc/en'
/usr/bin/meinproc --check --cache index.cache.bz2 ./index.docbook
make[3]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/doc/en'
make[2]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/doc'
Making all in po
make[2]: Entering directory `/home/gedg/Desktop/kxmame/trunk/po'
rm -f pl.gmo; /usr/bin/msgfmt -o pl.gmo ./pl.po
test ! -f pl.gmo || touch pl.gmo
rm -f it.gmo; /usr/bin/msgfmt -o it.gmo ./it.po
test ! -f it.gmo || touch it.gmo
rm -f zh_CN.gmo; /usr/bin/msgfmt -o zh_CN.gmo ./zh_CN.po
test ! -f zh_CN.gmo || touch zh_CN.gmo
rm -f sv.gmo; /usr/bin/msgfmt -o sv.gmo ./sv.po
test ! -f sv.gmo || touch sv.gmo
rm -f zh_TW.gmo; /usr/bin/msgfmt -o zh_TW.gmo ./zh_TW.po
test ! -f zh_TW.gmo || touch zh_TW.gmo
rm -f fr.gmo; /usr/bin/msgfmt -o fr.gmo ./fr.po
test ! -f fr.gmo || touch fr.gmo
rm -f de.gmo; /usr/bin/msgfmt -o de.gmo ./de.po
test ! -f de.gmo || touch de.gmo
rm -f es.gmo; /usr/bin/msgfmt -o es.gmo ./es.po
test ! -f es.gmo || touch es.gmo
rm -f el.gmo; /usr/bin/msgfmt -o el.gmo ./el.po
test ! -f el.gmo || touch el.gmo
rm -f nl.gmo; /usr/bin/msgfmt -o nl.gmo ./nl.po
test ! -f nl.gmo || touch nl.gmo
make[2]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/po'
Making all in src
make[2]: Entering directory `/home/gedg/Desktop/kxmame/trunk/src'
rm -rf DirTab.h;
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload ./DirTab.ui | /usr/bin/perl -pi -e "s,public QWizard,public KWizard,g; s,#include <qwizard.h>,#include <kwizard.h>,g" >> DirTab.h ;
rm -rf DisplayPref.h;
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload ./DisplayPref.ui | /usr/bin/perl -pi -e "s,public QWizard,public KWizard,g; s,#include <qwizard.h>,#include <kwizard.h>,g" >> DisplayPref.h ;
rm -rf GLrender.h;
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload ./GLrender.ui | /usr/bin/perl -pi -e "s,public QWizard,public KWizard,g; s,#include <qwizard.h>,#include <kwizard.h>,g" >> GLrender.h ;
rm -rf progress.h;
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload ./progress.ui | /usr/bin/perl -pi -e "s,public QWizard,public KWizard,g; s,#include <qwizard.h>,#include <kwizard.h>,g" >> progress.h ;
rm -rf sdlrender.h;
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload ./sdlrender.ui | /usr/bin/perl -pi -e "s,public QWizard,public KWizard,g; s,#include <qwizard.h>,#include <kwizard.h>,g" >> sdlrender.h ;
rm -rf soundpref.h;
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload ./soundpref.ui | /usr/bin/perl -pi -e "s,public QWizard,public KWizard,g; s,#include <qwizard.h>,#include <kwizard.h>,g" >> soundpref.h ;
rm -rf x11render.h;
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload ./x11render.ui | /usr/bin/perl -pi -e "s,public QWizard,public KWizard,g; s,#include <qwizard.h>,#include <kwizard.h>,g" >> x11render.h ;
rm -rf audit.h;
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload ./audit.ui | /usr/bin/perl -pi -e "s,public QWizard,public KWizard,g; s,#include <qwizard.h>,#include <kwizard.h>,g" >> audit.h ;
rm -rf vectorpref.h;
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload ./vectorpref.ui | /usr/bin/perl -pi -e "s,public QWizard,public KWizard,g; s,#include <qwizard.h>,#include <kwizard.h>,g" >> vectorpref.h ;
rm -rf ctrlpref.h;
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload ./ctrlpref.ui | /usr/bin/perl -pi -e "s,public QWizard,public KWizard,g; s,#include <qwizard.h>,#include <kwizard.h>,g" >> ctrlpref.h ;
rm -rf miscpref.h;
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload ./miscpref.ui | /usr/bin/perl -pi -e "s,public QWizard,public KWizard,g; s,#include <qwizard.h>,#include <kwizard.h>,g" >> miscpref.h ;
rm -rf startuppref.h;
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload ./startuppref.ui | /usr/bin/perl -pi -e "s,public QWizard,public KWizard,g; s,#include <qwizard.h>,#include <kwizard.h>,g" >> startuppref.h ;
rm -rf gameinfo.h;
/usr/share/qt3/bin/uic -L /usr/lib/kde3/plugins/designer -nounload ./gameinfo.ui | /usr/bin/perl -pi -e "s,public QWizard,public KWizard,g; s,#include <qwizard.h>,#include <kwizard.h>,g" >> gameinfo.h ;
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DKXMAME  -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.cpp; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
/usr/share/qt3/bin/moc ./kxmame.h -o kxmame.moc
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DKXMAME  -MT kxmame.o -MD -MP -MF ".deps/kxmame.Tpo" -c -o kxmame.o kxmame.cpp; \
        then mv -f ".deps/kxmame.Tpo" ".deps/kxmame.Po"; else rm -f ".deps/kxmame.Tpo"; exit 1; fi
/usr/share/qt3/bin/moc ./kxmameview.h -o kxmameview.moc
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DKXMAME  -MT kxmameview.o -MD -MP -MF ".deps/kxmameview.Tpo" -c -o kxmameview.o kxmameview.cpp; \
        then mv -f ".deps/kxmameview.Tpo" ".deps/kxmameview.Po"; else rm -f ".deps/kxmameview.Tpo"; exit 1; fi
/usr/share/qt3/bin/moc ./pref.h -o pref.moc
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DKXMAME  -MT pref.o -MD -MP -MF ".deps/pref.Tpo" -c -o pref.o pref.cpp; \
        then mv -f ".deps/pref.Tpo" ".deps/pref.Po"; else rm -f ".deps/pref.Tpo"; exit 1; fi
/usr/share/qt3/bin/moc ./dirselectiondialog.h -o dirselectiondialog.moc
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DKXMAME  -MT dirselectiondialog.o -MD -MP -MF ".deps/dirselectiondialog.Tpo" -c -o dirselectiondialog.o dirselectiondialog.cpp; \
        then mv -f ".deps/dirselectiondialog.Tpo" ".deps/dirselectiondialog.Po"; else rm -f ".deps/dirselectiondialog.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DKXMAME  -MT ColorListViewItem.o -MD -MP -MF ".deps/ColorListViewItem.Tpo" -c -o ColorListViewItem.o ColorListViewItem.cpp; \
        then mv -f ".deps/ColorListViewItem.Tpo" ".deps/ColorListViewItem.Po"; else rm -f ".deps/ColorListViewItem.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DKXMAME  -MT common_kxmame.o -MD -MP -MF ".deps/common_kxmame.Tpo" -c -o common_kxmame.o common_kxmame.cpp; \
        then mv -f ".deps/common_kxmame.Tpo" ".deps/common_kxmame.Po"; else rm -f ".deps/common_kxmame.Tpo"; exit 1; fi
/usr/share/qt3/bin/moc ./koselectaction.h -o koselectaction.moc
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DKXMAME  -MT koselectaction.o -MD -MP -MF ".deps/koselectaction.Tpo" -c -o koselectaction.o koselectaction.cpp; \
        then mv -f ".deps/koselectaction.Tpo" ".deps/koselectaction.Po"; else rm -f ".deps/koselectaction.Tpo"; exit 1; fi
/usr/share/qt3/bin/moc ./auditdialog.h -o auditdialog.moc
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DKXMAME  -MT auditdialog.o -MD -MP -MF ".deps/auditdialog.Tpo" -c -o auditdialog.o auditdialog.cpp; \
        then mv -f ".deps/auditdialog.Tpo" ".deps/auditdialog.Po"; else rm -f ".deps/auditdialog.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DKXMAME  -MT kxmamelogo.o -MD -MP -MF ".deps/kxmamelogo.Tpo" -c -o kxmamelogo.o kxmamelogo.cpp; \
        then mv -f ".deps/kxmamelogo.Tpo" ".deps/kxmamelogo.Po"; else rm -f ".deps/kxmamelogo.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -std=iso9899:1990 -W -Wall -Wchar-subscripts -Wshadow -Wpointer-arith -Wmissing-prototypes -Wwrite-strings -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -O2   -Wformat-security -Wmissing-format-attribute -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DKXMAME -MT unzip.o -MD -MP -MF ".deps/unzip.Tpo" -c -o unzip.o unzip.c; \
        then mv -f ".deps/unzip.Tpo" ".deps/unzip.Po"; else rm -f ".deps/unzip.Tpo"; exit 1; fi
/usr/share/qt3/bin/moc ./kxmamesnaptab.h -o kxmamesnaptab.moc
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DKXMAME  -MT kxmamesnaptab.o -MD -MP -MF ".deps/kxmamesnaptab.Tpo" -c -o kxmamesnaptab.o kxmamesnaptab.cpp; \
        then mv -f ".deps/kxmamesnaptab.Tpo" ".deps/kxmamesnaptab.Po"; else rm -f ".deps/kxmamesnaptab.Tpo"; exit 1; fi
/usr/share/qt3/bin/moc ./kxmame_joy.h -o kxmame_joy.moc
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DKXMAME  -MT kxmame_joy.o -MD -MP -MF ".deps/kxmame_joy.Tpo" -c -o kxmame_joy.o kxmame_joy.cpp; \
        then mv -f ".deps/kxmame_joy.Tpo" ".deps/kxmame_joy.Po"; else rm -f ".deps/kxmame_joy.Tpo"; exit 1; fi
/usr/include/linux/joystick.h:131: error: &#8216;__s64&#8217; does not name a type
/usr/include/linux/joystick.h:132: error: &#8216;__s64&#8217; does not name a type
make[2]: *** [kxmame_joy.o] Error 1
make[2]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gedg/Desktop/kxmame/trunk'
make: *** [all] Error 2
```

It seems I'm having some errors but I'm not sure what they are...

When I input "make install" this is what I get

```
Making install in doc
make[1]: Entering directory `/home/gedg/Desktop/kxmame/trunk/doc'
Making install in .
make[2]: Entering directory `/home/gedg/Desktop/kxmame/trunk/doc'
make[3]: Entering directory `/home/gedg/Desktop/kxmame/trunk/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/doc'
make[2]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/doc'
Making install in en
make[2]: Entering directory `/home/gedg/Desktop/kxmame/trunk/doc/en'
make[3]: Entering directory `/home/gedg/Desktop/kxmame/trunk/doc/en'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../admin/mkinstalldirs /usr/share/doc/HTML/en/kxmame
mkdir -p -- /usr/share/doc/HTML/en/kxmame
mkdir: cannot create directory `/usr/share/doc/HTML/en/kxmame': Permission denied
make[3]: *** [install-nls] Error 1
make[3]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/doc/en'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/doc/en'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/doc'
make: *** [install-recursive] Error 1
gedg@gedgPC:~/Desktop/kxmame/trunk$ sudo make install
[sudo] password for gedg:
Making install in doc
make[1]: Entering directory `/home/gedg/Desktop/kxmame/trunk/doc'
Making install in .
make[2]: Entering directory `/home/gedg/Desktop/kxmame/trunk/doc'
make[3]: Entering directory `/home/gedg/Desktop/kxmame/trunk/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/doc'
make[2]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/doc'
Making install in en
make[2]: Entering directory `/home/gedg/Desktop/kxmame/trunk/doc/en'
make[3]: Entering directory `/home/gedg/Desktop/kxmame/trunk/doc/en'
make[3]: Nothing to be done for `install-exec-am'.
/bin/bash ../../admin/mkinstalldirs /usr/share/doc/HTML/en/kxmame
mkdir -p -- /usr/share/doc/HTML/en/kxmame
/usr/bin/install -c -p -m 644 index.docbook /usr/share/doc/HTML/en/kxmame/index.docbook
/bin/bash ../../admin/mkinstalldirs /usr/share/doc/HTML/en/kxmame
/usr/bin/install -c -p -m 644 index.cache.bz2 /usr/share/doc/HTML/en/kxmame/
rm -f /usr/share/doc/HTML/en/kxmame/common
ln -s /usr/share/doc/kde/HTML/en/common /usr/share/doc/HTML/en/kxmame/common
make[3]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/doc/en'
make[2]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/doc/en'
make[1]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/doc'
Making install in po
make[1]: Entering directory `/home/gedg/Desktop/kxmame/trunk/po'
make[2]: Entering directory `/home/gedg/Desktop/kxmame/trunk/po'
make[2]: Nothing to be done for `install-exec-am'.
/usr/bin/install -c -p -m 644 pl.gmo /usr/share/locale/pl/LC_MESSAGES/kxmame.mo
/usr/bin/install -c -p -m 644 it.gmo /usr/share/locale/it/LC_MESSAGES/kxmame.mo
/usr/bin/install -c -p -m 644 zh_CN.gmo /usr/share/locale/zh_CN/LC_MESSAGES/kxmame.mo
/usr/bin/install -c -p -m 644 sv.gmo /usr/share/locale/sv/LC_MESSAGES/kxmame.mo
/usr/bin/install -c -p -m 644 zh_TW.gmo /usr/share/locale/zh_TW/LC_MESSAGES/kxmame.mo
/usr/bin/install -c -p -m 644 fr.gmo /usr/share/locale/fr/LC_MESSAGES/kxmame.mo
/usr/bin/install -c -p -m 644 de.gmo /usr/share/locale/de/LC_MESSAGES/kxmame.mo
/usr/bin/install -c -p -m 644 es.gmo /usr/share/locale/es/LC_MESSAGES/kxmame.mo
/usr/bin/install -c -p -m 644 el.gmo /usr/share/locale/el/LC_MESSAGES/kxmame.mo
/usr/bin/install -c -p -m 644 nl.gmo /usr/share/locale/nl/LC_MESSAGES/kxmame.mo
make[2]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/po'
make[1]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/po'
Making install in src
make[1]: Entering directory `/home/gedg/Desktop/kxmame/trunk/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DKXMAME  -MT kxmame_joy.o -MD -MP -MF ".deps/kxmame_joy.Tpo" -c -o kxmame_joy.o kxmame_joy.cpp; \
        then mv -f ".deps/kxmame_joy.Tpo" ".deps/kxmame_joy.Po"; else rm -f ".deps/kxmame_joy.Tpo"; exit 1; fi
/usr/include/linux/joystick.h:131: error: &#8216;__s64&#8217; does not name a type
/usr/include/linux/joystick.h:132: error: &#8216;__s64&#8217; does not name a type
make[1]: *** [kxmame_joy.o] Error 1
make[1]: Leaving directory `/home/gedg/Desktop/kxmame/trunk/src'
make: *** [install-recursive] Error 1
```

It seems I'm having similar errors...

EDIT#3: There is one point where I read permission denied so I tried with sudo...it's somewhere in the middle, gedg is my user name in case you think it's anything else...

---

### Post by DoktorSeven on 2008-03-03
Your "make" step didn't finish, note the error at the end. 

I've seen that you need to compile kxmame without joystick support (for the interface, not mame itself!) to get it to compile successfully.

Try 
```

./configure --disable-joystick

```

---

### Post by disturbedite on 2008-03-03
unless you're on 64bit, there is no reason to compile kxmame or sdlmame.
if you're on hardy, sdlmame has been available for a while in the ubuntu repo.
if not, you can ubuntu deb packages of sdlmame from here:
[http://wallyweek.altervista.org/](http://wallyweek.altervista.org/)

DoktorSeven has made a deb package of the kxmame build with sdlmame support.

if you search this forum you'll find the relevant threads & all the info you need.

---

### Post by Moonfrost on 2008-03-03
> **disturbedite said:**
> unless you're on 64bit, there is no reason to compile kxmame or sdlmame.
if you're on hardy, sdlmame has been available for a while in the ubuntu repo.
if not, you can ubuntu deb packages of sdlmame from here:
[http://wallyweek.altervista.org/](http://wallyweek.altervista.org/)

DoktorSeven has made a deb package of the kxmame build with sdlmame support.

if you search this forum you'll find the relevant threads & all the info you need.

Well I already have sdlmame working perfectly and I downloaded it from the same website of which you just posted a link from and it's working perfectly but I need kxmame so I don't have to use the terminal to start mame, so I can see all my games, use flyers snaps and such and be able to enable joystick...I'm not playing with the keyboard, I just bought a gamepad that works with Linux (I also have the wireless 360 controller which I use with the Windows version of mame) so I want to try it out with mame...

EDIT: By the way, the version of kxmame that I have is supposed to have support for sdlmame so yeah...

---

### Post by DoktorSeven on 2008-03-03
The joystick disable is for kxmame only, not SDLmame.  Joystick will still work fine in SDLmame, just not with the kxmame interface.

Perhaps someone can come up with a patch to fix this, but for now, the kxmame code as written does not compile unless you disable the joystick.

---

### Post by Moonfrost on 2008-03-03
> **DoktorSeven said:**
> The joystick disable is for kxmame only, not SDLmame.  Joystick will still work fine in SDLmame, just not with the kxmame interface.

Perhaps someone can come up with a patch to fix this, but for now, the kxmame code as written does not compile unless you disable the joystick.

Ok, but if I want to use a joystick with sdlmame I still have to enable it...as far as I know I have to do that with a frontend in this case kxmame...is there any way to do it anyway?

---

### Post by DoktorSeven on 2008-03-03
sdlmame should have joystick enabled anyway; if not, check the /etc/sdlmame/mame.ini file, (the line that says "joystick" should be set to 1).

---

### Post by disturbedite on 2008-03-05
> **Moonfrost said:**
> Ok, but if I want to use a joystick with sdlmame I still have to enable it...as far as I know I have to do that with a frontend in this case kxmame...is there any way to do it anyway?
i don't mean any offense by this, & don't take this the wrong way, but *of course you don't need a frontend to enable the joystick*.  as DoktorSeven said, you can enable it in the config file.

---

### Post by Moonfrost on 2008-03-05
> **disturbedite said:**
> i don't mean any offense by this, & don't take this the wrong way, but *of course you don't need a frontend to enable the joystick*.  as DoktorSeven said, you can enable it in the config file.

Well I didn't know since in Windows as far as I know in the command line version of mame you can't enable joystick...

---

### Post by DoktorSeven on 2008-03-06
Well, in SDLmame, you can definitely use the joystick.  The kxmame binary is only there to call the commandline SDLmame program which is completely separate, unlike the Windows all-in-one GUI/MAME programs (MAME32 and derivatives), thus all functionality has to be in SDLmame.

---

### Post by Holonet on 2008-03-12
I have gone through the exact same nonsense as the fellow who started this forum.  It really steams me when it says you need automake, I sit there for a couple hours trying to figure out what went wrong, and it ends up there are like 4 other things it's looking for as well which it didn't tell you.  I see no way of knowing that if you aren't familiar with Linux...anyway enough ranting :-D...

My issue now is this:

q@dualcorpse:~/Desktop/kxmame/trunk$ make -f Makefile.cvs
This Makefile is only for the CVS repository
This will be deleted before making the distribution

*** YOU'RE USING automake (GNU automake) 1.10.
*** KDE requires automake 1.6.1 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
q@dualcorpse:~/Desktop/kxmame/trunk$ 

Looking at the download site, automake 1.6.1 is from April 2002, now I know the repos are behind, but good lord...  1.10 is 2008...  This numbering system seems to be causing a problem...it's expecting that after 1.9.x, you go to 2.0...logical, yes?  Now it seems to think that 1.10 is older than 1.6.1....

I just installed 1.9.6 and it worked fine...someone needs smacking with a wet fish :-D.

---

