---
title: "KDE sig11 when emptying trash"
date: 2014-07-20
forum: Desktop Environments
---

### Post by Freek07 on 2014-07-20
After last update few days ago, KDE started crashing. sometimes it crashes when logging in, but it always crashes when I empty the trash.
Does anyone have any ideas?

```
Here's the log:

Application: Run Command Interface (krunner), signal: Segmentation fault
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[Current thread is 1 (Thread 0x7f16096a9800 (LWP 3225))]

Thread 2 (Thread 0x7f15eae20700 (LWP 3229)):
#0  0x00007f1608fbf6bd in read () at ../sysdeps/unix/syscall-template.S:81
#1  0x00007f15f7a36f45 in ?? () from /usr/lib/tls/libnvidia-tls.so.337.25
#2  0x00007f15fdf91c20 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f15fdf50b14 in g_main_context_check () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x00007f15fdf50f7b in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#5  0x00007f15fdf510ec in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#6  0x00007f1605de87be in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#7  0x00007f1605dba0af in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#8  0x00007f1605dba3a5 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#9  0x00007f1605cb6c5f in QThread::exec() () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#10 0x00007f1605d9b823 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#11 0x00007f1605cb932f in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#12 0x00007f15fe430182 in start_thread (arg=0x7f15eae20700) at pthread_create.c:312
#13 0x00007f1608fce30d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:111

Thread 1 (Thread 0x7f16096a9800 (LWP 3225)):
[KCrash Handler]
#5  0x00007f16040019af in KDirLister::Private::cachedItemsJobForUrl(KUrl const&) const () from /usr/lib/libkio.so.5
#6  0x00007f160400a3e9 in ?? () from /usr/lib/libkio.so.5
#7  0x00007f160400b3fb in ?? () from /usr/lib/libkio.so.5
#8  0x00007f1605dcf87a in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#9  0x00007f1604019345 in OrgKdeKDirNotifyInterface::FilesAdded(QString const&) () from /usr/lib/libkio.so.5
#10 0x00007f16040199a3 in OrgKdeKDirNotifyInterface::qt_metacall(QMetaObject::Call, int, void**) () from /usr/lib/libkio.so.5
#11 0x00007f16059e71f6 in ?? () from /usr/lib/x86_64-linux-gnu/libQtDBus.so.4
#12 0x00007f1605dd3c1e in QObject::event(QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#13 0x00007f16067ade2c in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
#14 0x00007f16067b44a0 in QApplication::notify(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
#15 0x00007f160808ad1a in KApplication::notify(QObject*, QEvent*) () from /usr/lib/libkdeui.so.5
#16 0x00007f1605dbb4dd in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#17 0x00007f1605dbeb3d in QCoreApplicationPrivate::sendPostedEvents(QObject*, int, QThreadData*) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#18 0x00007f1605de8f83 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#19 0x00007f15fdf50e04 in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#20 0x00007f15fdf51048 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#21 0x00007f15fdf510ec in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#22 0x00007f1605de87a1 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#23 0x00007f160684fbb6 in ?? () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
#24 0x00007f1605dba0af in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#25 0x00007f1605dba3a5 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#26 0x00007f1605dbfb79 in QCoreApplication::exec() () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#27 0x00007f16092c05a5 in kdemain () from /usr/lib/kde4/libkdeinit/libkdeinit4_krunner.so
#28 0x00007f1608ef4ec5 in __libc_start_main (main=0x4006d0, argc=1, argv=0x7fff732e9f48, init=<optimized out>, fini=<optimized out>, rtld_fini=<optimized out>, stack_end=0x7fff732e9f38) at libc-start.c:287
#29 0x00000000004006fe in _start ()
```

---

