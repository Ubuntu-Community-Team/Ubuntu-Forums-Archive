---
title: "Computer won't boot properly!"
date: 2009-02-06
forum: Desktop Environments
---

### Post by darkwolfalone on 2009-02-06
I upgraded to Kubuntu 8.10, installed Korean language support and set SKIM to start when KDE starts, and now KDE will not start properly. Please wonderful Ubuntu/Kubuntu community, save my life! I get the following error (I have no idea what it means): 

Application: Plasma Workspace (plasma), signal SIGSEGV
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
[New Thread 0xb54196c0 (LWP 6205)]
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
[KCrash handler]
#6  0xb70a1527 in QGraphicsLinearLayout::insertItem ()
   from /usr/lib/libQtGui.so.4
#7  0xb383f887 in ?? () from /usr/lib/kde4/plasma_applet_devicenotifier.so
#8  0xb383fa27 in ?? () from /usr/lib/kde4/plasma_applet_devicenotifier.so
#9  0xb7c4b585 in Plasma::Applet::flushPendingConstraintsEvents ()
   from /usr/lib/libplasma.so.2
#10 0xb7c4bbc6 in Plasma::Applet::timerEvent () from /usr/lib/libplasma.so.2
#11 0xb756b53f in QObject::event () from /usr/lib/libQtCore.so.4
#12 0xb70a4447 in QGraphicsWidget::event () from /usr/lib/libQtGui.so.4
#13 0xb6ae48ec in QApplicationPrivate::notify_helper ()
   from /usr/lib/libQtGui.so.4
#14 0xb6aec72e in QApplication::notify () from /usr/lib/libQtGui.so.4
#15 0xb7a2ab2d in KApplication::notify () from /usr/lib/libkdeui.so.5
#16 0xb755be61 in QCoreApplication::notifyInternal ()
   from /usr/lib/libQtCore.so.4
#17 0xb7589d81 in ?? () from /usr/lib/libQtCore.so.4
#18 0xb7586520 in ?? () from /usr/lib/libQtCore.so.4
#19 0xb58aa6f8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#20 0xb58adda3 in ?? () from /usr/lib/libglib-2.0.so.0
#21 0xb58adf61 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#22 0xb7586478 in QEventDispatcherGlib::processEvents ()
   from /usr/lib/libQtCore.so.4
#23 0xb6b7eea5 in ?? () from /usr/lib/libQtGui.so.4
#24 0xb755a52a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#25 0xb755a6ea in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#26 0xb679a3eb in KIO::NetAccess::enter_loop () from /usr/lib/libkio.so.5
#27 0xb679a5ec in KIO::NetAccess::statInternal () from /usr/lib/libkio.so.5
#28 0xb679b3fb in KIO::NetAccess::stat () from /usr/lib/libkio.so.5
#29 0xb679b47b in KIO::NetAccess::mostLocalUrl () from /usr/lib/libkio.so.5
#30 0xb3892f1e in ?? () from /usr/lib/kde4/plasma_applet_icon.so
#31 0xb38936ff in ?? () from /usr/lib/kde4/plasma_applet_icon.so
#32 0xb7c7b737 in Plasma::Corona::loadLayout () from /usr/lib/libplasma.so.2
#33 0xb7c7c531 in Plasma::Corona::initializeLayout ()
   from /usr/lib/libplasma.so.2
#34 0xb7ee1199 in ?? () from /usr/lib/libkdeinit4_plasma.so
#35 0xb7ee2880 in ?? () from /usr/lib/libkdeinit4_plasma.so
#36 0xb7ee4a81 in ?? () from /usr/lib/libkdeinit4_plasma.so
#37 0xb7ed643a in kdemain () from /usr/lib/libkdeinit4_plasma.so
#38 0x080485b2 in _start ()
#0  0xb7f1f430 in __kernel_vsyscall ()

---

### Post by the_ice.e on 2009-03-23
Hi

I have instalated kubuntu 8.10 on my laptop and it worked great..
I split the partition once so now i have 2 of the same size (+swap) but thats not the problem probably.

The problem I think its when I instalated some programs and the adapt
(nothing big.. just some programs for music editing and things like that).
It prompt me if I shutdown the x server or the option to restart later for changes to take effect.
I chose to restart later and so I did restart.
The splash screen was on until it goes into loading (hope u get it XP)
And then it boots in text form :S

I get asked for the user name and password (like in terminal) and I login.
But there is no desktop no mouse no nothing.. just to write commands..

Now I instalated another kubuntu 8.10 on the second partition to post :D

Help?!

---

