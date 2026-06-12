---
title: "Plasma Workspace (plasma), signal SIGSEGV"
date: 2008-12-12
forum: Desktop Environments
---

### Post by ToddAndMargo on 2008-12-12
Hi All,

I am running KDE4.1 in kubunto.  After an update (maybe, I am not sure),
I can no longer get KDE to load.  Error is :Plasma Workspace (plasma),
signal SIGSEGV 11.

XFce works.  But, I'd like to get KDE back as well.

How do I fix this?

Many thanks,
-T

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
[New Thread 0xb54636c0 (LWP 4977)]
[New Thread 0xb3818b90 (LWP 4982)]
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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb70ec414 in QGraphicsLinearLayout::setSpacing ()
   from /usr/lib/libQtGui.so.4
#7  0xb383c368 in ?? () from /usr/lib/kde4/plasma_applet_notes.so
#8  0xb383c410 in ?? () from /usr/lib/kde4/plasma_applet_notes.so
#9  0xb7c96585 in Plasma::Applet::flushPendingConstraintsEvents ()
   from /usr/lib/libplasma.so.2
#10 0xb7c96bc6 in Plasma::Applet::timerEvent () from /usr/lib/libplasma.so.2
#11 0xb75b653f in QObject::event () from /usr/lib/libQtCore.so.4
#12 0xb70ef447 in QGraphicsWidget::event () from /usr/lib/libQtGui.so.4
#13 0xb6b2f8ec in QApplicationPrivate::notify_helper ()
   from /usr/lib/libQtGui.so.4
#14 0xb6b3772e in QApplication::notify () from /usr/lib/libQtGui.so.4
#15 0xb7a75b2d in KApplication::notify () from /usr/lib/libkdeui.so.5
#16 0xb75a6e61 in QCoreApplication::notifyInternal ()
   from /usr/lib/libQtCore.so.4
#17 0xb75d4d81 in ?? () from /usr/lib/libQtCore.so.4
#18 0xb75d1520 in ?? () from /usr/lib/libQtCore.so.4
#19 0xb58f46f8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#20 0xb58f7da3 in ?? () from /usr/lib/libglib-2.0.so.0
#21 0xb58f7f61 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#22 0xb75d1478 in QEventDispatcherGlib::processEvents ()
   from /usr/lib/libQtCore.so.4
#23 0xb6bc9ea5 in ?? () from /usr/lib/libQtGui.so.4
#24 0xb75a552a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#25 0xb75a56ea in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#26 0xb67e43eb in KIO::NetAccess::enter_loop () from /usr/lib/libkio.so.5
#27 0xb67e45ec in KIO::NetAccess::statInternal () from /usr/lib/libkio.so.5
#28 0xb67e53fb in KIO::NetAccess::stat () from /usr/lib/libkio.so.5
#29 0xb67e547b in KIO::NetAccess::mostLocalUrl () from /usr/lib/libkio.so.5
#30 0xb3847f1e in ?? () from /usr/lib/kde4/plasma_applet_icon.so
#31 0xb38486ff in ?? () from /usr/lib/kde4/plasma_applet_icon.so
#32 0xb7cc6737 in Plasma::Corona::loadLayout () from /usr/lib/libplasma.so.2
#33 0xb7cc7531 in Plasma::Corona::initializeLayout ()
   from /usr/lib/libplasma.so.2
#34 0xb7f2c199 in ?? () from /usr/lib/libkdeinit4_plasma.so
#35 0xb7f2d880 in ?? () from /usr/lib/libkdeinit4_plasma.so
#36 0xb7f2fa81 in ?? () from /usr/lib/libkdeinit4_plasma.so
#37 0xb7f2143a in kdemain () from /usr/lib/libkdeinit4_plasma.so
#38 0x080485b2 in _start ()
#0  0xb7f68430 in __kernel_vsyscall ()

---

### Post by ToddAndMargo on 2008-12-13
Figured it out.

mv .kde .kde.000

start over

---

