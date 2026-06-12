---
title: "Plasma Work space crashing"
date: 2011-03-11
forum: Desktop Environments
---

### Post by Jonny87 on 2011-03-11
Every time I boot my computer, I'm greeted with the KDE crash handler poping up telling me that Plasma Workspace has crashed.

I have followed the bug reporting process.

Can anyone understand the following, and work out whats causing it?
```
 p, li { white-space: pre-wrap; } Application: Plasma Workspace (plasma-desktop), signal: Segmentation fault
 [Current thread is 1 (Thread 0x7fde439e97a0 (LWP 1996))]
  Thread 3 (Thread 0x7fde1aeba700 (LWP 1998)):
 #0  0x00007fde432fa203 in __poll (fds=<value optimized out>, nfds=<value optimized out>, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:87
 #1  0x00007fde37ee4009 in ?? () from /lib/libglib-2.0.so.0
 #2  0x00007fde37ee445c in g_main_context_iteration () from /lib/libglib-2.0.so.0
 #3  0x00007fde409af1e6 in QEventDispatcherGlib::processEvents (this=0x2cc9280, flags=<value optimized out>) at kernel/qeventdispatcher_glib.cpp:417
 #4  0x00007fde40981a02 in QEventLoop::processEvents (this=<value optimized out>, flags=) at kernel/qeventloop.cpp:149
 #5  0x00007fde40981dec in QEventLoop::exec (this=0x7fde1aeb9cb0, flags=) at kernel/qeventloop.cpp:201
 #6  0x00007fde4088c2fd in QThread::exec (this=<value optimized out>) at thread/qthread.cpp:490
 #7  0x00007fde409615f8 in QInotifyFileSystemWatcherEngine::run (this=0x2c9be50) at io/qfilesystemwatcher_inotify.cpp:248
 #8  0x00007fde4088f27e in QThreadPrivate::start (arg=0x2c9be50) at thread/qthread_unix.cpp:266
 #9  0x00007fde3b541953 in ?? () from /usr/lib/nvidia-current/libGL.so.1
 #10 0x00007fde40604971 in start_thread (arg=<value optimized out>) at pthread_create.c:304
 #11 0x00007fde4330692d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
 #12 0x0000000000000000 in ?? ()
  Thread 2 (Thread 0x7fde14524700 (LWP 2053)):
 #0  0x00007fff3528e904 in clock_gettime ()
 #1  0x00007fde381860bf in clock_gettime (clock_id=1, tp=0x7fde145239e0) at ../sysdeps/unix/clock_gettime.c:100
 #2  0x00007fde408e494f in do_gettime () at tools/qelapsedtimer_unix.cpp:105
 #3  qt_gettime () at tools/qelapsedtimer_unix.cpp:119
 #4  0x00007fde409b11fd in QTimerInfoList::updateCurrentTime (this=0x1) at kernel/qeventdispatcher_unix.cpp:339
 #5  0x00007fde409b1225 in QTimerInfoList::timerWait (this=0x1, tm=...) at kernel/qeventdispatcher_unix.cpp:442
 #6  0x00007fde409af3dd in timerSourcePrepareHelper (src=<value optimized out>, timeout=0x7fde14523b1c) at kernel/qeventdispatcher_glib.cpp:136
 #7  0x00007fde409af485 in timerSourcePrepare (source=0x1, timeout=0x7fde145239e0) at kernel/qeventdispatcher_glib.cpp:169
 #8  0x00007fde37ee3a11 in g_main_context_prepare () from /lib/libglib-2.0.so.0
 #9  0x00007fde37ee3e78 in ?? () from /lib/libglib-2.0.so.0
 #10 0x00007fde37ee445c in g_main_context_iteration () from /lib/libglib-2.0.so.0
 #11 0x00007fde409af1e6 in QEventDispatcherGlib::processEvents (this=0x325f7e0, flags=<value optimized out>) at kernel/qeventdispatcher_glib.cpp:417
 #12 0x00007fde40981a02 in QEventLoop::processEvents (this=<value optimized out>, flags=) at kernel/qeventloop.cpp:149
 #13 0x00007fde40981dec in QEventLoop::exec (this=0x7fde14523cb0, flags=) at kernel/qeventloop.cpp:201
 #14 0x00007fde4088c2fd in QThread::exec (this=<value optimized out>) at thread/qthread.cpp:490
 #15 0x00007fde409615f8 in QInotifyFileSystemWatcherEngine::run (this=0x33e4820) at io/qfilesystemwatcher_inotify.cpp:248
 #16 0x00007fde4088f27e in QThreadPrivate::start (arg=0x33e4820) at thread/qthread_unix.cpp:266
 #17 0x00007fde3b541953 in ?? () from /usr/lib/nvidia-current/libGL.so.1
 #18 0x00007fde40604971 in start_thread (arg=<value optimized out>) at pthread_create.c:304
 #19 0x00007fde4330692d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
 #20 0x0000000000000000 in ?? ()
  Thread 1 (Thread 0x7fde439e97a0 (LWP 1996)):
 [KCrash Handler]
 #6  0x00007fde19e58c5c in ?? () from /usr/lib/kde4/plasma_applet_message_indicator.so
 #7  0x00007fde40982507 in QCoreApplicationPrivate::sendThroughObjectEventFilters (this=<value optimized out>, receiver=0x6a978e0, event=0x7fff35211b40) at kernel/qcoreapplication.cpp:847
 #8  0x00007fde3faccfac in QApplicationPrivate::notify_helper (this=0x2189670, receiver=0x6a978e0, e=0x7fff35211b40) at kernel/qapplication.cpp:4392
 #9  0x00007fde3fad2aed in QApplication::notify (this=0x2170060, receiver=0x6a978e0, e=0x7fff35211b40) at kernel/qapplication.cpp:4277
 #10 0x00007fde4161e156 in KApplication::notify (this=0x2170060, receiver=0x6a978e0, event=0x7fff35211b40) at ../../kdeui/kernel/kapplication.cpp:310
 #11 0x00007fde40982cdc in QCoreApplication::notifyInternal (this=0x2170060, receiver=0x6a978e0, event=0x7fff35211b40) at kernel/qcoreapplication.cpp:732
 #12 0x00007fde3fb18bf1 in sendEvent (this=0x6a978e0, action=0x2be2e20) at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:215
 #13 QWidget::removeAction (this=0x6a978e0, action=0x2be2e20) at kernel/qwidget.cpp:3169
 #14 0x00007fde3ff2d350 in QMenu::clear (this=<value optimized out>) at widgets/qmenu.cpp:1714
 #15 0x00007fde39207324 in DBusMenuImporter::GetChildrenCallback(int, QDBusPendingCallWatcher*) () from /usr/lib/libdbusmenu-qt.so.2
 #16 0x00007fde39206315 in DBusMenuImporter::dispatch(QDBusPendingCallWatcher*) () from /usr/lib/libdbusmenu-qt.so.2
 #17 0x00007fde3920a9dc in DBusMenuImporter::qt_metacall(QMetaObject::Call, int, void**) () from /usr/lib/libdbusmenu-qt.so.2
 #18 0x00007fde4099ab27 in QMetaObject::activate (sender=0x36682a0, m=<value optimized out>, local_signal_index=<value optimized out>, argv=0x1) at kernel/qobject.cpp:3280
 #19 0x00007fde40d1337f in QDBusPendingCallWatcher::finished (this=0x34322e0, _t1=0x36682a0) at .moc/release-shared/moc_qdbuspendingcall.cpp:92
 #20 0x00007fde40d13409 in _q_finished (this=0x36682a0, _c=QMetaObject::InvokeMetaMethod, _id=<value optimized out>, _a=0x3ac14c0) at qdbuspendingcall.cpp:482
 #21 QDBusPendingCallWatcher::qt_metacall (this=0x36682a0, _c=QMetaObject::InvokeMetaMethod, _id=<value optimized out>, _a=0x3ac14c0) at .moc/release-shared/moc_qdbuspendingcall.cpp:80
 #22 0x00007fde40994bde in QObject::event (this=0x36682a0, e=0x34322e0) at kernel/qobject.cpp:1219
 #23 0x00007fde3faccfdc in QApplicationPrivate::notify_helper (this=0x2189670, receiver=0x36682a0, e=0x36e7280) at kernel/qapplication.cpp:4396
 #24 0x00007fde3fad2aed in QApplication::notify (this=0x2170060, receiver=0x36682a0, e=0x36e7280) at kernel/qapplication.cpp:4277
 #25 0x00007fde4161e156 in KApplication::notify (this=0x2170060, receiver=0x36682a0, event=0x36e7280) at ../../kdeui/kernel/kapplication.cpp:310
 #26 0x00007fde40982cdc in QCoreApplication::notifyInternal (this=0x2170060, receiver=0x36682a0, event=0x36e7280) at kernel/qcoreapplication.cpp:732
 #27 0x00007fde40985c22 in sendEvent (receiver=0x0, event_type=<value optimized out>, data=0x2119560) at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:215
 #28 QCoreApplicationPrivate::sendPostedEvents (receiver=0x0, event_type=<value optimized out>, data=0x2119560) at kernel/qcoreapplication.cpp:1373
 #29 0x00007fde409af653 in sendPostedEvents (s=0x218cdc0) at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:220
 #30 postEventSourceDispatch (s=0x218cdc0) at kernel/qeventdispatcher_glib.cpp:277
 #31 0x00007fde37ee0342 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
 #32 0x00007fde37ee42a8 in ?? () from /lib/libglib-2.0.so.0
 #33 0x00007fde37ee445c in g_main_context_iteration () from /lib/libglib-2.0.so.0
 #34 0x00007fde409af193 in QEventDispatcherGlib::processEvents (this=0x2119070, flags=<value optimized out>) at kernel/qeventdispatcher_glib.cpp:415
 #35 0x00007fde3fb7fa4e in QGuiEventDispatcherGlib::processEvents (this=0x34322e0, flags=<value optimized out>) at kernel/qguieventdispatcher_glib.cpp:204
 #36 0x00007fde40981a02 in QEventLoop::processEvents (this=<value optimized out>, flags=) at kernel/qeventloop.cpp:149
 #37 0x00007fde40981dec in QEventLoop::exec (this=0x7fff35212970, flags=) at kernel/qeventloop.cpp:201
 #38 0x00007fde40985ebb in QCoreApplication::exec () at kernel/qcoreapplication.cpp:1009
 #39 0x00007fde435dda56 in kdemain (argc=<value optimized out>, argv=<value optimized out>) at ../../../../plasma/desktop/shell/main.cpp:118
 #40 0x00007fde4323ed8e in __libc_start_main (main=<value optimized out>, argc=<value optimized out>, ubp_av=<value optimized out>, init=<value optimized out>, fini=<value optimized out>, rtld_fini=<value optimized out>, stack_end=0x7fff35212d38) at libc-start.c:226
 #41 0x0000000000400669 in _start ()
 
```

---

### Post by Zorael on 2011-03-13
Try reporting the bug and see if it finds any duplicate entries. If not, just file it.

Remember, unreported bugs can only be fixed by accident.

---

### Post by Jonny87 on 2011-03-15
I've done that, as well as tried updating. Still getting it every day. I don't mind getting my hands dirty if to fix it if someone can point me in the right direction to fix it.

---

