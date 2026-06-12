---
title: "Dock issues"
date: 2005-10-18
forum: Desktop Environments
---

### Post by escobar on 2005-10-18
Hello,

I am attempting to get a working dock. Either KSmoothDock or Kooldock,at this point I don't think I care which. The problem I run into with Kooldock is after I download it, untar it, switch to it's directory and type './ configure' then it swiches me back to the Kooldock directory as if I didn't type anything. the problem with KSmoothDock is I take all the above steps, but it won't compile. It keeps saying 'no C compiler found'.I have GCC installed so I don't quite understand what it's referring to. Looking over previous posts and such, most have had more success than me so I know I'm missing something. Question is what?

Also, I tried kxdocker or whatever it's called. I did mannage to get that one to launch but it's so buggy it's unusable. Thanks again.

---

### Post by escobar on 2005-10-19
*bump*

After more googling and searching I stil haven't found anything. Any help would be much appreciated.

---

### Post by GeneralZod on 2005-10-19
Have you done 

```

sudo apt-get install build-essential

```

?

---

### Post by escobar on 2005-10-19
No, I re-call trying to add that earlier, per the Ubuntu Guide but it wasn't in any of the repositories. I since then added some and enabled universe and multi-verse, so I will give it another try when I get home. I'll let everyone know how it goes.

---

### Post by escobar on 2005-10-20
Here's what I did to make it work:

sudo apt-get install build-essential as suggested earlier. Then, sudo apt-get install libqt3-mt-dev libqt3-compat-headers kdelibs4-dev kdebase-dev. I found this info in this thread:

[http://www.ubuntuforums.org/showthread.php?t=45408](http://www.ubuntuforums.org/showthread.php?t=45408)

After that change to the ksmoothdock directory. Run:

./configure
make
sudo make install

-Everything compiled fine. From the official ksmoothdock instruction from kde-look.org say you should be able to run it by typing 'ksmoothdock' into the 'run' menu. That didn't work for me, so I ran a find for 'ksmoothdock' and double-clicked the executable once I found it. That got it to launch. Took me about 5 minutes or so to figure out how to configure it the way I want. Once I did that, I placed a link the ksmoothdock executable in my autostart folder so it launches when I log into Kubuntu. That's pretty much. Dock works really well too. I hope this saves someone time and frustration. Maybe add this to the "how to" section?

-Thanks again to all who helped.

---

### Post by escobar on 2005-10-20
Here's what I did to make it work:

sudo apt-get install build-essential as suggested earlier. Then, sudo apt-get install libqt3-mt-dev libqt3-compat-headers kdelibs4-dev kdebase-dev. I found this info in this thread:

[http://www.ubuntuforums.org/showthread.php?t=45408](http://www.ubuntuforums.org/showthread.php?t=45408)

After that change to the ksmoothdock directory. Run:

./configure
make
sudo make install

 Everything compiled fine. From the official ksmoothdock instruction from kde-look.org says you should be able to run it by typing 'ksmoothdock' into the 'run' menu. That didn't work for me, so I ran a find for 'ksmoothdock' and double-clicked the executable once I found it. That got it to launch. Took me about 5 minutes or so to figure out how to configure it the way I wanted. 

 Once I did that, I placed a link to the ksmoothdock executable in my 'autostart' folder so it launches when I log into Kubuntu. That's pretty much it. Dock works really well too. I hope this saves someone time and frustration. 

Maybe add this to the "how to" section?

-Thanks again to all who helped.

---

### Post by acejones on 2005-10-20
that doesn't work for me.  

sorry this is going to be long

when i run make, this is what i get:
```

acejones@H4CK3R:~/ksmoothdock-3.6.beta/ksmoothdock$ make
make  all-recursive
make[1]: Entering directory `/home/acejones/ksmoothdock-3.6.beta/ksmoothdock'
Making all in doc
make[2]: Entering directory `/home/acejones/ksmoothdock-3.6.beta/ksmoothdock/doc'
Making all in .
make[3]: Entering directory `/home/acejones/ksmoothdock-3.6.beta/ksmoothdock/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/acejones/ksmoothdock-3.6.beta/ksmoothdock/doc'
Making all in en
make[3]: Entering directory `/home/acejones/ksmoothdock-3.6.beta/ksmoothdock/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/acejones/ksmoothdock-3.6.beta/ksmoothdock/doc/en'
make[2]: Leaving directory `/home/acejones/ksmoothdock-3.6.beta/ksmoothdock/doc'
Making all in po
make[2]: Entering directory `/home/acejones/ksmoothdock-3.6.beta/ksmoothdock/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/acejones/ksmoothdock-3.6.beta/ksmoothdock/po'
Making all in src
make[2]: Entering directory `/home/acejones/ksmoothdock-3.6.beta/ksmoothdock/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.cpp; \
then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT ksmoothdock.o -MD -MP -MF ".deps/ksmoothdock.Tpo" -c -o ksmoothdock.o ksmoothdock.cpp; \
then mv -f ".deps/ksmoothdock.Tpo" ".deps/ksmoothdock.Po"; else rm -f ".deps/ksmoothdock.Tpo"; exit 1; fi
In file included from /usr/include/c++/4.0.2/backward/iostream.h:31,
                 from ksmoothdock.cpp:18:
/usr/include/c++/4.0.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
ksmoothdock.cpp:528: warning: unused parameter ‘e’
ksmoothdock.cpp:741: warning: unused parameter ‘e’
ksmoothdock.cpp: In member function ‘void KSmoothDock::mousePressEventNZ(QMouseEvent*)’:
ksmoothdock.cpp:1236: warning: ‘setActiveWindow’ is deprecated (declared at /usr/include/kde/kwin.h:113)
ksmoothdock.cpp:1246: warning: ‘info’ is deprecated (declared at /usr/include/kde/kwin.h:493)
ksmoothdock.cpp:1246: warning: ‘setTitle’ is deprecated (declared at /usr/include/kde/kpopupmenu.h:200)
ksmoothdock.cpp: In member function ‘void KSmoothDock::mousePressEventPZ(QMouseEvent*)’:
ksmoothdock.cpp:1352: warning: ‘setActiveWindow’ is deprecated (declared at /usr/include/kde/kwin.h:113)
ksmoothdock.cpp:1374: warning: ‘info’ is deprecated (declared at /usr/include/kde/kwin.h:493)
ksmoothdock.cpp:1374: warning: ‘setTitle’ is deprecated (declared at /usr/include/kde/kpopupmenu.h:200)
ksmoothdock.cpp: At global scope:
ksmoothdock.cpp:1406: warning: unused parameter ‘e’
ksmoothdock.cpp: In member function ‘void KSmoothDock::mouseMoveEventPZ(QMouseEvent*)’:
ksmoothdock.cpp:1582: warning: ‘setActiveWindow’ is deprecated (declared at /usr/include/kde/kwin.h:113)
ksmoothdock.cpp:1751: warning: comparison between signed and unsigned integer expressions
ksmoothdock.cpp:1764: warning: comparison between signed and unsigned integer expressions
ksmoothdock.cpp: In member function ‘void KSmoothDock::timerTickedPZ()’:
ksmoothdock.cpp:1786: warning: comparison between signed and unsigned integer expressions
ksmoothdock.cpp: In member function ‘void KSmoothDock::continueZoomOut()’:
ksmoothdock.cpp:1828: warning: ‘setActiveWindow’ is deprecated (declared at /usr/include/kde/kwin.h:113)
ksmoothdock.cpp: In member function ‘void KSmoothDock::enterEventNZ(QEvent*)’:
ksmoothdock.cpp:1868: warning: ‘setActiveWindow’ is deprecated (declared at /usr/include/kde/kwin.h:113)
ksmoothdock.cpp: At global scope:
ksmoothdock.cpp:1867: warning: unused parameter ‘e’
ksmoothdock.cpp:1873: warning: unused parameter ‘e’
ksmoothdock.cpp:1918: warning: unused parameter ‘e’
ksmoothdock.cpp:1947: warning: unused parameter ‘e’
ksmoothdock.cpp: In member function ‘void KSmoothDock::windowAdded(WId)’:
ksmoothdock.cpp:2068: warning: ‘info’ is deprecated (declared at /usr/include/kde/kwin.h:493)
ksmoothdock.cpp:2068: warning: ‘info’ is deprecated (declared at /usr/include/kde/kwin.h:493)
ksmoothdock.cpp: In member function ‘void KSmoothDock::windowChanged(WId, unsigned int)’:
ksmoothdock.cpp:2119: warning: ‘info’ is deprecated (declared at /usr/include/kde/kwin.h:493)
ksmoothdock.cpp:2119: warning: ‘info’ is deprecated (declared at /usr/include/kde/kwin.h:493)
ksmoothdock.cpp:2122: warning: ‘info’ is deprecated (declared at /usr/include/kde/kwin.h:493)
ksmoothdock.cpp:2134: warning: ‘info’ is deprecated (declared at /usr/include/kde/kwin.h:493)
ksmoothdock.cpp:2136: warning: ‘info’ is deprecated (declared at /usr/include/kde/kwin.h:493)
ksmoothdock.cpp:2161: warning: ‘info’ is deprecated (declared at /usr/include/kde/kwin.h:493)
ksmoothdock.cpp: In member function ‘void KSmoothDock::addTask(WId)’:
ksmoothdock.cpp:2444: warning: ‘info’ is deprecated (declared at /usr/include/kde/kwin.h:493)
ksmoothdock.cpp: At global scope:
ksmoothdock.cpp:2806: warning: unused parameter ‘pix’
ksmoothdock.cpp:2905: warning: unused parameter ‘desktop’
ksmoothdock.cpp: In member function ‘void KSmoothDock::showWindowStack()’:
ksmoothdock.cpp:3055: warning: ‘info’ is deprecated (declared at /usr/include/kde/kwin.h:493)
ksmoothdock.cpp: In member function ‘void KSmoothDock::paintEventNZ(QPaintEvent*)’:
ksmoothdock.cpp:531: warning: ‘sw’ may be used uninitialized in this function
ksmoothdock.cpp:531: warning: ‘sx’ may be used uninitialized in this function
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT confdialog.o -MD -MP -MF ".deps/confdialog.Tpo" -c -o confdialog.o confdialog.cpp; \
then mv -f ".deps/confdialog.Tpo" ".deps/confdialog.Po"; else rm -f ".deps/confdialog.Tpo"; exit 1; fi
/usr/share/qt3/include/qtooltip.h:86: warning: ‘class QToolTip’ has virtual functions but non-virtual destructor
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT tooltip.o -MD -MP -MF ".deps/tooltip.Tpo" -c -o tooltip.o tooltip.cpp; \
then mv -f ".deps/tooltip.Tpo" ".deps/tooltip.Po"; else rm -f ".deps/tooltip.Tpo"; exit 1; fi
In file included from /usr/include/c++/4.0.2/backward/iostream.h:31,
                 from tooltip.cpp:23:
/usr/include/c++/4.0.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
/bin/sh ../libtool --silent --mode=link --tag=CXX g++  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common    -o ksmoothdock -R /usr/lib -R /usr/share/qt3/lib -R /usr/X11R6/lib -L/usr/X11R6/lib -L/usr/share/qt3/lib -L/usr/lib  main.o ksmoothdock.o aboutdialog.o confdialog.o confkickerdialog.o confmenudialog.o item.o showdesktop.o tooltip.o welcomedialog.o confkickerdialog.moc.o welcomedialog.moc.o confdialog.moc.o tooltip.moc.o aboutdialog.moc.o ksmoothdock.moc.o  -lkdeui
confmenudialog.o: In function `ConfMenuDialog::ConfMenuDialog(QWidget*, char const*, bool, unsigned int)':
confmenudialog.cpp:(.text+0x147c): undefined reference to `KIconButton::KIconButton(QWidget*, char const*)'
confmenudialog.o: In function `ConfMenuDialog::ConfMenuDialog(QWidget*, char const*, bool, unsigned int)':
confmenudialog.cpp:(.text+0x1f2c): undefined reference to `KIconButton::KIconButton(QWidget*, char const*)'
confmenudialog.o: In function `ConfMenuDialog::btAdd_clicked()':
confmenudialog.cpp:(.text+0x273b): undefined reference to `KIconButton::setIcon(QString const&)'
confmenudialog.o: In function `ConfMenuDialog::btRemove_clicked()':
confmenudialog.cpp:(.text+0x2bbc): undefined reference to `KIconButton::setIcon(QString const&)'
confmenudialog.o: In function `ConfMenuDialog::btBrowse_clicked()':
confmenudialog.cpp:(.text+0x314a): undefined reference to `KFileDialog::getOpenFileName(QString const&, QString const&, QWidget*, QString const&)'
confmenudialog.o: In function `ConfMenuDialog::selectedItemChanged()':
confmenudialog.cpp:(.text+0x32fc): undefined reference to `KIconButton::setIcon(QString const&)'
confmenudialog.o: In function `ConfMenuDialog::update()':
confmenudialog.cpp:(.text+0x357c): undefined reference to `KIconButton::setIcon(QString const&)'
collect2: ld returned 1 exit status
make[2]: *** [ksmoothdock] Error 1
make[2]: Leaving directory `/home/acejones/ksmoothdock-3.6.beta/ksmoothdock/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/acejones/ksmoothdock-3.6.beta/ksmoothdock'
make: *** [all] Error 2
```

---

### Post by escobar on 2005-10-20
*Off the top of my head*

Did you run ./configure first? I'm not an expert with Ubuntu but I'll help you if I can.

---

### Post by acejones on 2005-10-20
yep

---

### Post by Navyblue on 2005-10-21
I got the same exact error he had.

---

### Post by escobar on 2005-10-21
Well to be honest gentleman I am out of ideas. Perhaps a more seasoned user can assist?

---

### Post by acejones on 2005-10-21
no big deal

on my windows boxes i use Y'z dock and love it.  i've actually got kxdocker installed in kubuntu, but its sooooo slooooowwww (but its my machine).  i've also tried kroller with karamba, but for some reason it never comes up.  so, so far i haven't found anything except adding a panel at the bottom and making it transparent and hiding it.

---

