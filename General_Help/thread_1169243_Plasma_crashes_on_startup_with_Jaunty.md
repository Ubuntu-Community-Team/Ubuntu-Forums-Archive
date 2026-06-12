---
title: "Plasma crashes on startup with Jaunty"
date: 2009-05-25
forum: General Help
---

### Post by GameKyuubi on 2009-05-25
Plasma crashes after I login (immediately after the loading bar finishes) and the system just sits there.  I can still launch programs through alt-F2, but when I try to start Plasma again I get some notifications that pass by too fast to read and then a single repeating error that pushes the rest off the screen.

The repeating error is
plasma(4450): ""min" - conversion of "-1,-1" to QSizeF failed"
plasma(4450): ""max" - conversion of "-1,-1" to QSizeF failed"
plasma(4450): ""min" - conversion of "-1,-1" to QSizeF failed"
plasma(4450): ""max" - conversion of "-1,-1" to QSizeF failed"
plasma(4450): ""min" - conversion of "-1,-1" to QSizeF failed"
plasma(4450): ""max" - conversion of "-1,-1" to QSizeF failed"

And then the string of errors ends with
plasma(4449): Communication problem with  "plasma" , it probably crashed.
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" "

Does anyone know what is going on?  Furthermore, how can I grab the log from this crash?

---

### Post by GameKyuubi on 2009-05-25
Figured out a workaround.  Removing

.kde/share/config/plasmarc
.kde/share/config/plasma-appletsrc

let Plasma start.

---

### Post by pavel.horal on 2009-06-01
If you delete this configuration files you will lost your plasma settings (for example desktop notes).

I have same problem (no plasma after login). I use double screen at my work (twinview) and when i come home, sometimes my notebook (disconnected from external display) has this error.

So i've discovered, that in ~/.kde/share/config/plasmarc there are PlasmaViews definitions. When i delete the definition of my external display everything is ok. 

If you don't want to find wich settings have gone bad I suggest try to delete file ~/.kde/share/config/plasmarc first.

---

### Post by Pollywoggy on 2009-06-03
> **pavel.horal said:**
> If you delete this configuration files you will lost your plasma settings (for example desktop notes).

I have same problem (no plasma after login). I use double screen at my work (twinview) and when i come home, sometimes my notebook (disconnected from external display) has this error.

So i've discovered, that in ~/.kde/share/config/plasmarc there are PlasmaViews definitions. When i delete the definition of my external display everything is ok. 

If you don't want to find wich settings have gone bad I suggest try to delete file ~/.kde/share/config/plasmarc first.

I just reinstalled  Jaunty and now I have this problem, with Plasma crashing when I start KDE.  I looked in ~/.kde/share/config and I do not even have the files plasmarc or any file beginning with "plasma" there.
I can start my desktop by bringing up krunner and entering "plasma.kde4"

---

### Post by JohnnyKRK on 2009-06-09
> **Pollywoggy said:**
> I just reinstalled Jaunty and now I have this problem, with Plasma crashing when I start KDE. I looked in ~/.kde/share/config and I do not even have the files plasmarc or any file beginning with "plasma" there.
I can start my desktop by bringing up krunner and entering "plasma.kde4"
 
Hello,
I got also crashing plasma problem, the above solution with moving plasmarc stuff did not work for me either.
I am using Kubuntu with:
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 9.04
Release: 9.04
Codename: jaunty
uname -a
2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
plasma --version
<unknown program name>(3445)/: Cannot connect to the X server
Qt: 4.5.0
KDE: 4.2.2 (KDE 4.2.2)
Przestrze&#324; robocza Plazmy: 0.3
 
The problem occured after I did apt-get install update. Maybe I used wrong repositories.
```

# deb cdrom:[Kubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) jaunty main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) jaunty-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/jr/ppa/ubuntu](http://ppa.launchpad.net/jr/ppa/ubuntu) jaunty main 

```
Then I remotelly with ssh via putty restarted my PC. I remember that I got some programs opened like ogmrip and firefox.
I can see the following critical error report:
```

Ten &#9532;&#356;lad czynno&#9532;&#356;ci wygl&#9472;&#367;da na bezu&#9532;&#9565;yteczny.
Jest tak zapewne dlatego, &#9532;&#9565;e Twoje pakiety zosta&#9532;éy utworzone w taki spos&#9500;&#9474;b, by uniemo&#9532;&#9565;liwi&#9472;ç tworzenie poprawnych &#9532;&#356;lad&#9500;&#9474;w czynno&#9532;&#356;ci. Mo&#9532;&#9565;e to by&#9472;ç spowodowane tak&#9532;&#9565;e bardzo powa&#9532;&#9565;n&#9472;&#367; awari&#9472;&#367; programu, kt&#9500;&#9474;ra spowodowa&#9532;éa uszkodzenie &#9532;&#356;ladu.
[Thread debugging using libthread_db enabled]
[New Thread 0xb4c09710 (LWP 3054)]
[New Thread 0xa939ab90 (LWP 3055)]
0xb7f82430 in __kernel_vsyscall ()
[Current thread is 0 (LWP 3054)]
Thread 2 (Thread 0xa939ab90 (LWP 3055)):
#0  0xb7f82430 in __kernel_vsyscall ()
#1  0xb511c0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb62d42ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb64c09b2 in QWaitCondition::wait (this=0x90d4490, mutex=0x90d448c, time=4294967295) at thread/qwaitcondition_unix.cpp:87
#4  0xb7941152 in QHostInfoAgent::run (this=0x90d4480) at kernel/qhostinfo.cpp:260
#5  0xb64bf96e in QThreadPrivate::start (arg=0x90d4480) at thread/qthread_unix.cpp:189
#6  0xb51184ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb62c549e in clone () from /lib/tls/i686/cmov/libc.so.6
Thread 1 (Thread 0xb4c09710 (LWP 3054)):
#0  0xb7f82430 in __kernel_vsyscall ()
#1  0xb62807a6 in nanosleep () from /lib/tls/i686/cmov/libc.so.6
#2  0xb62805be in sleep () from /lib/tls/i686/cmov/libc.so.6
#3  0xb77288b2 in KCrash::startDrKonqi (argv=0xbfc9c6b4, argc=17) at /build/buildd/kde4libs-4.2.2/kdeui/util/kcrash.cpp:412
#4  0xb7729274 in KCrash::defaultCrashHandler (sig=11) at /build/buildd/kde4libs-4.2.2/kdeui/util/kcrash.cpp:337
#5  <signal handler called>
#6  0xb6e94cc1 in QGraphicsItem::setVisible (this=0x8, visible=<value optimized out>) at graphicsview/qgraphicsitem.cpp:1620
#7  0xa9596312 in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#8  0xa9596c01 in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#9  0xa959923e in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#10 0xa959d522 in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#11 0xa959085c in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#12 0xa9590e54 in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#13 0xa9581085 in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#14 0xa958658f in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#15 0xa958809c in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#16 0xa95891f4 in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#17 0xa958a14c in ?? () from /usr/lib/kde4/plasma_applet_networkmanagement.so
#18 0xb7dd79a7 in Plasma::Corona::loadLayout () from /usr/lib/libplasma.so.3
#19 0xb7dd9131 in Plasma::Corona::initializeLayout () from /usr/lib/libplasma.so.3
#20 0xb7f42a1d in PlasmaApp::corona (this=0x8d730b8) at /build/buildd/kdebase-workspace-4.2.2/plasma/shells/desktop/plasmaapp.cpp:514
#21 0xb7f43035 in PlasmaApp::setupDesktop (this=0x8d730b8) at /build/buildd/kdebase-workspace-4.2.2/plasma/shells/desktop/plasmaapp.cpp:255
#22 0xb7f4656b in PlasmaApp::qt_metacall (this=0x8d730b8, _c=QMetaObject::InvokeMetaMethod, _id=2, _a=0xbfc9d798)
    at /build/buildd/kdebase-workspace-4.2.2/obj-i486-linux-gnu/plasma/shells/desktop/plasmaapp.moc:95
#23 0xb65c9ca8 in QMetaObject::activate (sender=0x8ddbdc8, from_signal_index=4, to_signal_index=4, argv=0x0) at kernel/qobject.cpp:3069
#24 0xb65ca932 in QMetaObject::activate (sender=0x8ddbdc8, m=0xb66a5908, local_signal_index=0, argv=0x0) at kernel/qobject.cpp:3143
#25 0xb65cf0a7 in QSingleShotTimer::timeout (this=0x8ddbdc8) at .moc/release-shared/qtimer.moc:76
#26 0xb65cf1cc in QSingleShotTimer::timerEvent (this=0x8ddbdc8) at kernel/qtimer.cpp:298
#27 0xb65c415f in QObject::event (this=0x8ddbdc8, e=0xbfc9dc1c) at kernel/qobject.cpp:1082
#28 0xb6860e9c in QApplicationPrivate::notify_helper (this=0x8d6db68, receiver=0x8ddbdc8, e=0xbfc9dc1c) at kernel/qapplication.cpp:4084
#29 0xb686919e in QApplication::notify (this=0x8d730b8, receiver=0x8ddbdc8, e=0xbfc9dc1c) at kernel/qapplication.cpp:3631
#30 0xb76b894d in KApplication::notify (this=0x8d730b8, receiver=0x8ddbdc8, event=0xbfc9dc1c) at /build/buildd/kde4libs-4.2.2/kdeui/kernel/kapplication.cpp:307
#31 0xb65b3a3b in QCoreApplication::notifyInternal (this=0x8d730b8, receiver=0x8ddbdc8, event=0xbfc9dc1c) at kernel/qcoreapplication.cpp:602
#32 0xb65e2d71 in QTimerInfoList::activateTimers (this=0x8d749ac) at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:213
#33 0xb65df4e0 in timerSourceDispatch (source=0x8d74978) at kernel/qeventdispatcher_glib.cpp:164
#34 0xb4f16b88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#35 0xb4f1a0eb in ?? () from /usr/lib/libglib-2.0.so.0
#36 0xb4f1a268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#37 0xb65df438 in QEventDispatcherGlib::processEvents (this=0x8d370f0, flags={i = -1077289576}) at kernel/qeventdispatcher_glib.cpp:323
#38 0xb6902365 in QGuiEventDispatcherGlib::processEvents (this=0x8d370f0, flags={i = -1077289528}) at kernel/qguieventdispatcher_glib.cpp:202
#39 0xb65b206a in QEventLoop::processEvents (this=0xbfc9de40, flags={i = -1077289464}) at kernel/qeventloop.cpp:149
#40 0xb65b24aa in QEventLoop::exec (this=0xbfc9de40, flags={i = -1077289400}) at kernel/qeventloop.cpp:200
#41 0xb65b4959 in QCoreApplication::exec () at kernel/qcoreapplication.cpp:880
#42 0xb6860d17 in QApplication::exec () at kernel/qapplication.cpp:3553
#43 0xb7f2eb56 in kdemain (argc=1, argv=0xbfc9dff4) at /build/buildd/kdebase-workspace-4.2.2/plasma/shells/desktop/main.cpp:54
#44 0x08048712 in main (argc=) at /build/buildd/kdebase-workspace-4.2.2/obj-i486-linux-gnu/plasma/shells/desktop/plasma_qgv_dummy.cpp:3
#0  0xb7f82430 in __kernel_vsyscall () 

```
Thanks for any help.
regards
Johnny

---

### Post by Pollywoggy on 2009-06-09
Some people have reported that uninstalling the network management applet fixed it for them.  That did not work for me.  I just bring up krunner (Alt-f2) and put "plasma.kde4" in the box and execute the command, each time I start KDE.

---

### Post by JohnnyKRK on 2009-06-10
> **Pollywoggy said:**
> Some people have reported that uninstalling the network management applet fixed it for them. That did not work for me. I just bring up krunner (Alt-f2) and put "plasma.kde4" in the box and execute the command, each time I start KDE.
Thanks,
Ok I will try to remove network management applet but does it mean I will have no network connection anymore? 
btw how to uninstall it. I suppose I should run ```
sudo apt-get remove NameOfPackage
``` but what is the name of this applet.
 
If it won't work do you think there will be some fix for this issue in a future or we will have to each time start plasma.kde4 manually.

---

### Post by Pollywoggy on 2009-06-10
> **JohnnyKRK said:**
> Thanks,
Ok I will try to remove network management applet but does it mean I will have no network connection anymore? 
btw how to uninstall it. I suppose I should run ```
sudo apt-get remove NameOfPackage
``` but what is the name of this applet.
 
If it won't work do you think there will be some fix for this issue in a future or we will have to each time start plasma.kde4 manually.

I think it will probably be fixed but it will probably require an upstream fix since it does not seem to be a problem in just *ubuntu.  It affects other Linux distributions too.

---

