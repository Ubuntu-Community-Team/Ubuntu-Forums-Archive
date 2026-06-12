---
title: "KDevelop and Gnome"
date: 2005-11-17
forum: Desktop Environments
---

### Post by dpm on 2005-11-17
Hi,

I'm using the "standard" Breezy flavour with GNOME as a desktop environment, and I was checking out some development tools. Although Anjuta + Glade work like a charm, I thought I'd give KDevelop a go. But I seem to be missing some package or something, because I cannot get it to run.

I've installed the following packages (all from synaptic, with main, universe, multiverse and backports enabled):

cvs (1:1.12.9-13ubuntu1)
kdebase-bin (4:3.4.3-0ubuntu6)
kdevelop3 (4:3.2.3-0ubuntu2)
kdevelop3-data (4:3.2.3-0ubuntu2)
kdevelop3-plugins (4:3.2.3-0ubuntu2)
libcvsservice0 (4:3.4.3-0ubuntu1)

Here I got the first problems, so I installed this:
kdevelop3-dev (4:3.2.3-0ubuntu2)

That did not work, either, so I installed the qt3 libraries:
libaudio-dev (1.7-2ubuntu2)
libgl1-mesa-dev (6.3.2-0ubuntu6breezy1)
libglu1-mesa-dev (6.3.2-0ubuntu6breezy1)
liblcms1-dev (1.13-1)
libmng-dev (1.0.8-1)
libqt3-headers (3:3.3.4-8ubuntu5)
libqt3-mt-dev (3:3.3.4-8ubuntu5)
libxmu-dev (1:6.2.3-5)
libxmu-headers (1:6.2.3-5)
libxt-dev (1:0.99.0+cvs.20050803-3)
qt3-dev-tools (3:3.3.4-8ubuntu5)
x11proto-gl-dev (1.4+cvs.20050524-5)
xlibs-static-dev (6.8.2-77)

So far, I've had no luck, I always get the following error messages when trying to run, for example, KDevelop Assistant:[INDENT]**There was an error setting up inter-process communications for KDE. The message returned by the system was:**
  
  **Could not read network connection list.**
  **/home/dpm/.DCOPserver_ubuntu__0**
  
  **Please check that the "dcopserver" program is running!**
[/INDENT]I've also attached a few screenshots with the messages I'm getting.

I'm thinking this dcopserver thingy might be what is needed (the error messages seem to make it quite obvious), but I havent't got a clue what it is. Any ideas, anyone?

Thanks.

---

### Post by metoo on 2005-11-18
Don't see the kdelibs stuff in your list.
If you really want to check out the KDE stuff, install kubuntu-desktop, it will solve all of your problems but will install a lot of things you are not interested in.

kdebase might be an alternative to start with, and/or kdelibs-bin

At the moment, doesn't apt-get show any problems?
Doesn't
apt-get -f install
want's to install any other packages?

I use (and like) KDevelop3, but I develop with Qt/KDE and don't know the other package you mentioned.

---

### Post by dpm on 2005-11-19
Many thanks for your reply, metoo.

As I said, I just wanted to check KDevelop3 out, if possible without installing lots of extra packages which I won't use. I think your suggestion of installing kubuntu-desktop is probably the solution, but I do not want to convert my ubuntu installation to kubuntu, I'm quite happy with gnome at the moment (and I'm afraid installing kubuntu-desktop might break it :shock:).

I think there might be an easier, more lightweight solution, some package (or a couple of them) I'm missing. I'll keep trying. Meanwhile, any comments will be very welcome again.

Oh, and the output of apt-get -f install was the following:

**apt-get -f install**
[B]Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/B]

BTW, in the meantime I found out what DCOPserver is (quoting from kde.org):

>  dcopserver is a deamon which provides inter-process communication (DCOP) facilities to all KDE applications. The DCOP facilities are accessible from the command shell via the [ dcop]("http://www-106.ibm.com/developerworks/linux/library/l-dcop/index.html?ca=dgr-kdeml01KDEDCOP") command line tool. DCOP is essential for all KDE applications.

---

### Post by dpm on 2005-11-19
Quick reply:

The kdelibs were already on my system:
kdelibs4c2
kdelibs-bin
kdelibs-data

In addition to that, I installed
kdelibs

which didn't seem to help at all.

BTW, I'm not sure if this makes any difference, but the kdevelop3 package I installed is from the *universe* repositories. There must be an "official" ubuntu kdevelop package buried underneath one of those metapackages from *main*, but I just can't find it!!! I think I'm giving up...

---

### Post by dpm on 2005-11-20
I did not give up... :D

I solved this issue by changing the ownership of everything in the .kde hidden directory in my home directory. For some strange reason, most of the folders were owned by root, so I *chown*ed them to my user name, and now the dcopserver can start and kdevelop3 works.

Mind you, the KDevelop assistant still crashes for some unknown reason, but that does not bother me (well.. a bit), because I can run the IDE with no problems.

I really do not know what caused all those files and directories in .kde to be *chown*ed to root, but I noticed that this issue affected also other KDE apps, which would not run before. Now they seem to work after the changes.

Anyway, if anyone has got any clue to what causes kdevassistant to crash, I'd be very grateful. Thx.

BTW, here's the backtrace of the crash, as listed by the KDE Crash Handler:

> (no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1239513408 (LWP 9417)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#4  0xb64c3ef1 in XCreateGC () from /usr/lib/libX11.so.6
#5  0xb69328bb in qsincos () from /usr/lib/libqt-mt.so.3
#6  0xb6932ee0 in qsincos () from /usr/lib/libqt-mt.so.3
#7  0xb6933301 in QPainter::updatePen () from /usr/lib/libqt-mt.so.3
#8  0xb69ebd8f in QPainter::setPen () from /usr/lib/libqt-mt.so.3
#9  0xb6b1fd54 in QSplashScreen::drawContents () from /usr/lib/libqt-mt.so.3
#10 0xb6b1f910 in QSplashScreen::drawContents () from /usr/lib/libqt-mt.so.3
#11 0xb6b1f969 in QSplashScreen::repaint () from /usr/lib/libqt-mt.so.3
#12 0xb6b1faff in QSplashScreen::setPixmap () from /usr/lib/libqt-mt.so.3
#13 0xb6b1fc52 in QSplashScreen::QSplashScreen () from /usr/lib/libqt-mt.so.3
#14 0xb7fa30af in SplashScreen::SplashScreen ()
   from /usr/lib/libkdevshell.so.0
#15 0x08049fbd in ?? ()
#16 0x0814c980 in ?? ()
#17 0xbfcc8ad4 in ?? ()
#18 0x00000000 in ?? ()
#19 0x00000000 in ?? ()
#20 0x00000000 in ?? ()
#21 0x00000001 in ?? ()
#22 0x0804abb4 in vtable for QGList ()
#23 0x0804ab3d in vtable for QGList ()
#24 0x0804a402 in vtable for QGList ()
#25 0x0804a3ee in vtable for QGList ()
#26 0x00000008 in ?? ()
#27 0x00000004 in ?? ()
#28 0xb644fcd0 in ?? () from /usr/lib/libstdc++.so.6
#29 0xb6342908 in __malloc_initialize_hook ()
   from /lib/tls/i686/cmov/libc.so.6
#30 0x00000002 in ?? ()
#31 0x00000015 in ?? ()
#32 0x00000005 in ?? ()
#33 0xb715f7e8 in vtable for KApplication () from /usr/lib/libkdecore.so.4
#34 0x00000020 in ?? ()
#35 0x08133ba0 in ?? ()
#36 0x00000000 in ?? ()
#37 0x08073210 in ?? ()
#38 0x08138680 in ?? ()
#39 0x08137548 in ?? ()
#40 0x0814a240 in ?? ()
#41 0x08073288 in ?? ()
#42 0x00000000 in ?? ()
#43 0x00000001 in ?? ()
#44 0x0805aa80 in ?? ()
#45 0x08049100 in ?? ()
#46 0x00000000 in ?? ()
#47 0x0815c298 in ?? ()
#48 0x080bd4c0 in ?? ()
#49 0x081327c0 in ?? ()
#50 0xb6227a00 in ?? () from /lib/tls/i686/cmov/libc.so.6
#51 0xb715f864 in vtable for KApplication () from /usr/lib/libkdecore.so.4
#52 0x081342a0 in ?? ()
#53 0x08134100 in ?? ()
#54 0x081402c8 in ?? ()
#55 0xb6e774e0 in vtable for QCString () from /usr/lib/libqt-mt.so.3
#56 0x08133d38 in ?? ()
#57 0xbfcc8aa0 in ?? ()
#58 0x08133b88 in ?? ()
#59 0x0805b858 in ?? ()
#60 0x000001da in ?? ()
#61 0x000000df in ?? ()
#62 0xb61ef544 in ?? ()
#63 0x00000000 in ?? ()
#64 0x0804ef98 in ?? ()
#65 0x08049101 in ?? ()
#66 0x00000000 in ?? ()
#67 0x00000000 in ?? ()
#68 0xb7fb51ac in ?? ()
#69 0xbfcc8b28 in ?? ()
#70 0xb7fbd7c9 in _dl_rtld_di_serinfo () from /lib/ld-linux.so.2
#71 0xb622bea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#72 0x08049701 in ?? ()


---

