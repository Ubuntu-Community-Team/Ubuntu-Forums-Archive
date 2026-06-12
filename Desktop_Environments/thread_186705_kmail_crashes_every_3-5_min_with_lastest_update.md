---
title: "kmail crashes every 3-5 min with lastest update"
date: 2006-06-02
forum: Desktop Environments
---

### Post by harty83 on 2006-06-02
Hello,

I did an update yesterday which updated the majority of my kde applciations but now kmail will not stay open for more than 3-5 mintues without it crashing.  Is anyone else having this problem?  Any advice on how to solve?

Here is the backtrace:

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
[New Thread -1248024896 (LWP 17355)]
[New Thread -1276785744 (LWP 17390)]
[New Thread -1268393040 (LWP 17389)]
[New Thread -1260000336 (LWP 17388)]
[New Thread -1251607632 (LWP 17387)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#6  0xb7c1f9b3 in KMMessage::transferInProgress ()
   from /usr/lib/libkmailprivate.so
#7  0xb7e156ae in KMMoveCommand::execute () from /usr/lib/libkmailprivate.so
#8  0xb7e08d32 in KMCommand::slotPostTransfer ()
   from /usr/lib/libkmailprivate.so
#9  0xb7e0e78f in KMCommand::qt_invoke () from /usr/lib/libkmailprivate.so
#10 0xb7e0e9ff in KMMenuCommand::qt_invoke () from /usr/lib/libkmailprivate.so
#11 0xb7e0ea74 in KMMoveCommand::qt_invoke () from /usr/lib/libkmailprivate.so
#12 0xb7154e29 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#13 0xb7e07d0c in KMCommand::messagesTransfered ()
   from /usr/lib/libkmailprivate.so
#14 0xb7e0e341 in KMCommand::transferSelectedMsgs ()
   from /usr/lib/libkmailprivate.so
#15 0xb7e0e599 in KMCommand::slotStart () from /usr/lib/libkmailprivate.so
#16 0xb7e0e7a1 in KMCommand::qt_invoke () from /usr/lib/libkmailprivate.so
#17 0xb7e0e9ff in KMMenuCommand::qt_invoke () from /usr/lib/libkmailprivate.so
#18 0xb7e0ea74 in KMMoveCommand::qt_invoke () from /usr/lib/libkmailprivate.so
#19 0xb7154e29 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#20 0xb74e7e1a in QSignal::signal () from /usr/lib/libqt-mt.so.3
#21 0xb71725a0 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#22 0xb717a090 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#23 0xb70eadc6 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#24 0xb70eafc2 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#25 0xb77e8e31 in KApplication::notify () from /usr/lib/libkdecore.so.4
#26 0xb707c0ef in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#27 0xb70dc7b3 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#28 0xb708feff in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#29 0xb71038b7 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#30 0xb71037da in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#31 0xb70e98d5 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#32 0x0804a04b in ?? ()
#33 0xbfbcace8 in ?? ()
#34 0xbfbcaed4 in ?? ()
#35 0x00000000 in ?? ()

```

Thanks!

---

### Post by harty83 on 2006-06-03
fixed by deleting /home/myusername/.kde

---

