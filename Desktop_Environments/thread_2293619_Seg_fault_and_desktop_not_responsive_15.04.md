---
title: "Seg fault and desktop not responsive 15.04"
date: 2015-09-06
forum: Desktop Environments
---

### Post by buddy123 on 2015-09-06
Out of the blue :o My Kubuntu is behaving strange.
My desktop is not responsive. the bars and menu items all working OK, but the desktop itself (where the background image is) isnt.
I have a crash log, perhaps it can shed some light

```

Application: Plasma (plasmashell), signal: Aborted
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[Current thread is 1 (Thread 0x7f39b76817c0 (LWP 1361))]


Thread 4 (Thread 0x7f39a33f8700 (LWP 1363)):
#0  0x00007f39b242a8dd in poll () at ../sysdeps/unix/syscall-template.S:81
#1  0x00007f39b4997b72 in ?? () from /usr/lib/x86_64-linux-gnu/libxcb.so.1
#2  0x00007f39b499964f in xcb_wait_for_event () from /usr/lib/x86_64-linux-gnu/libxcb.so.1
#3  0x00007f39a573f099 in ?? () from /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqxcb.so
#4  0x00007f39b2aabb0e in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#5  0x00007f39b1cb16aa in start_thread (arg=0x7f39a33f8700) at pthread_create.c:333
#6  0x00007f39b2435eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109


Thread 3 (Thread 0x7f39a091e700 (LWP 1388)):
#0  0x00007f39b242a8dd in poll () at ../sysdeps/unix/syscall-template.S:81
#1  0x00007f39aeb36ebc in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f39aeb36fcc in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f39b2d42c6c in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#4  0x00007f39b2ce73e2 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#5  0x00007f39b2aa6b44 in QThread::exec() () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#6  0x00007f39b4834f65 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#7  0x00007f39b2aabb0e in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#8  0x00007f39b1cb16aa in start_thread (arg=0x7f39a091e700) at pthread_create.c:333
#9  0x00007f39b2435eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109


Thread 2 (Thread 0x7f398d57b700 (LWP 1400)):
#0  0x00007f39b242a8dd in poll () at ../sysdeps/unix/syscall-template.S:81
#1  0x00007f39aeb36ebc in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f39aeb36fcc in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f39b2d42c6c in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#4  0x00007f39b2ce73e2 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#5  0x00007f39b2aa6b44 in QThread::exec() () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#6  0x00007f39b4834f65 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
#7  0x00007f39b2aabb0e in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#8  0x00007f39b1cb16aa in start_thread (arg=0x7f398d57b700) at pthread_create.c:333
#9  0x00007f39b2435eed in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109


Thread 1 (Thread 0x7f39b76817c0 (LWP 1361)):
[KCrash Handler]
#6  0x00007f39b2364267 in __GI_raise (sig=sig@entry=6) at ../sysdeps/unix/sysv/linux/raise.c:55
#7  0x00007f39b2365eca in __GI_abort () at abort.c:89
#8  0x00007f39b275a06d in __gnu_cxx::__verbose_terminate_handler() () from /usr/lib/x86_64-linux-gnu/libstdc++.so.6
#9  0x00007f39b2757ee6 in ?? () from /usr/lib/x86_64-linux-gnu/libstdc++.so.6
#10 0x00007f39b2757f31 in std::terminate() () from /usr/lib/x86_64-linux-gnu/libstdc++.so.6
#11 0x00007f39b2758a7f in __cxa_pure_virtual () from /usr/lib/x86_64-linux-gnu/libstdc++.so.6
#12 0x00007f39b302396a in QPlatformScreen::physicalSize() const () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
#13 0x00007f39b305d7b2 in QScreen::physicalSize() const () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
#14 0x00007f39b305d869 in QScreen::physicalDotsPerInch() const () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
#15 0x00007f39b74a4c49 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
#16 0x00007f39b2d1a9c9 in QMetaObject::activate(QObject*, int, int, void**) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#17 0x00007f39b303ad4f in QWindow::screenChanged(QScreen*) () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
#18 0x00007f39b303b5a5 in QWindowPrivate::emitScreenChangedRecursion(QScreen*) () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
#19 0x00007f39b303ecc3 in QWindowPrivate::setTopLevelScreen(QScreen*, bool) () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
#20 0x00007f39b303ee65 in QWindow::screenDestroyed(QObject*) () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
#21 0x00007f39b2d1a35a in QMetaObject::activate(QObject*, int, int, void**) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#22 0x00007f39b2d1b0ff in QObject::destroyed(QObject*) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#23 0x00007f39b2d23a8b in QObject::~QObject() () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#24 0x00007f39b305d679 in QScreen::~QScreen() () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
#25 0x00007f39b3023f2a in QPlatformScreen::~QPlatformScreen() () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
#26 0x00007f39a574a769 in ?? () from /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqxcb.so
#27 0x00007f39a573d5ab in ?? () from /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqxcb.so
#28 0x00007f39a573e27d in ?? () from /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqxcb.so
#29 0x00007f39a573f4bb in ?? () from /usr/lib/x86_64-linux-gnu/qt5/plugins/platforms/libqxcb.so
#30 0x00007f39b2d1b73a in QObject::event(QEvent*) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#31 0x00007f39b35f3b2c in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5
#32 0x00007f39b35f9000 in QApplication::notify(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5
#33 0x00007f39b2ce9c2b in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#34 0x00007f39b2cebc9b in QCoreApplicationPrivate::sendPostedEvents(QObject*, int, QThreadData*) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#35 0x00007f39b2d42843 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#36 0x00007f39aeb36c3d in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#37 0x00007f39aeb36f20 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#38 0x00007f39aeb36fcc in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#39 0x00007f39b2d42c57 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#40 0x00007f39b2ce73e2 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#41 0x00007f39b2cef02c in QCoreApplication::exec() () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
#42 0x000000000042fd9b in main ()



```

Im not sure what more info is required. Any guidance is accepted.
Thanks in advance

---

