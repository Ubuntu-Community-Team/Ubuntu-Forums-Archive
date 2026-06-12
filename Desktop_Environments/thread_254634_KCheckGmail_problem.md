---
title: "KCheckGmail problem"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Guillaumeb on 2006-09-10
hi all,

I have Ubuntu on which I have installed KDE. My default envirronment is Gnome. Some KDE apps like kaffeine works perfectly. I have installed KCheckGmail but, though it is listed in the Internet Applications, it does not work.

I really like this notifier though and I was wondering if there was a way to make it work with Gnome.

thank you

---

### Post by robert114 on 2006-11-02
Are you using 64 bit version and do you get an error like this in the KDE crash handler:
```
(no debugging symbols found)
(no debugging symbols found)
0x000000394e594c40 in nanosleep () from /lib/libc.so.6
#0  0x000000394e594c40 in nanosleep () from /lib/libc.so.6
#1  0x000000394e594a94 in sleep () from /lib/libc.so.6
#2  0x0000003b0fa07575 in KCrash::startDrKonqi ()
   from /usr/lib/libkdecore.so.4
#3  0x0000003b0fa1bb07 in KCrash::defaultCrashHandler ()
   from /usr/lib/libkdecore.so.4
#4  0x000000394e530510 in killpg () from /lib/libc.so.6
#5  0x0000000000000000 in ?? ()
```

---

### Post by scubastevegk on 2007-05-21
I am!  Here's what I'm getting in the crash handler - any ideas?

```
(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
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
[New Thread 47168285846032 (LWP 9243)]
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
#5  0x00002ae634fa2c16 in QString::fromUtf8 () from /usr/lib/libqt-mt.so.3
#6  0x00002ae634fa8396 in QString::sprintf () from /usr/lib/libqt-mt.so.3
#7  0x0000000000414894 in ?? ()
#8  0x00000000004171a8 in ?? ()
#9  0x00000000004183f1 in ?? ()
#10 0x00002ae634c9fce2 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#11 0x00002ae632590d32 in KIO::Job::result () from /usr/lib/libkio.so.4
#12 0x00002ae6325cae9f in KIO::Job::emitResult () from /usr/lib/libkio.so.4
#13 0x00002ae6325d6aca in KIO::SimpleJob::slotFinished ()
   from /usr/lib/libkio.so.4
#14 0x00002ae6325d711a in KIO::TransferJob::slotFinished ()
   from /usr/lib/libkio.so.4
#15 0x00002ae6325cab08 in KIO::TransferJob::qt_invoke ()
   from /usr/lib/libkio.so.4
#16 0x00002ae634c9fce2 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#17 0x00002ae634ca087c in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#18 0x00002ae6325ef445 in KIO::SlaveInterface::dispatch ()
   from /usr/lib/libkio.so.4
#19 0x00002ae6325e031e in KIO::SlaveInterface::dispatch ()
   from /usr/lib/libkio.so.4
#20 0x00002ae63259f24b in KIO::Slave::gotInput () from /usr/lib/libkio.so.4
#21 0x00002ae6325e36c8 in KIO::Slave::qt_invoke () from /usr/lib/libkio.so.4
#22 0x00002ae634c9fce2 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#23 0x00002ae634ca06d3 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#24 0x00002ae63500ea20 in QSocketNotifier::activated ()
   from /usr/lib/libqt-mt.so.3
#25 0x00002ae634cc1640 in QSocketNotifier::event ()
   from /usr/lib/libqt-mt.so.3
#26 0x00002ae634c3b1d6 in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#27 0x00002ae634c3cf65 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#28 0x00002ae6339bd7a8 in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#29 0x00002ae634bcdcc2 in QApplication::sendEvent ()
   from /usr/lib/libqt-mt.so.3
#30 0x00002ae634c2ddef in QEventLoop::activateSocketNotifiers ()
   from /usr/lib/libqt-mt.so.3
#31 0x00002ae634be23d0 in QEventLoop::processEvents ()
   from /usr/lib/libqt-mt.so.3
#32 0x00002ae634c5470b in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#33 0x00002ae634c54513 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#34 0x00002ae634c3cc9c in QApplication::exec () from /usr/lib/libqt-mt.so.3
#35 0x000000000040d746 in ?? ()
#36 0x00002ae63835b8e4 in __libc_start_main () from /lib/libc.so.6
#37 0x000000000040d509 in ?? ()
#38 0x00007fff788d9408 in ?? ()
#39 0x0000000000000000 in ?? ()

```

---

