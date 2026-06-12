---
title: "Raki crashes"
date: 2006-02-06
forum: Desktop Environments
---

### Post by theFallen on 2006-02-06
After getting synce to work, I thoought I made it. Wrong :D
Neverending troubles. Does sombody know what happens here?

> 
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
[Thread debugging using libthread_db enabled]
[New Thread -1233037632 (LWP 21148)]
[KCrash handler]
#6  0x08077315 in Rra::getTypes ()
#7  0x0806f228 in PDA::getSynchronizationTypes ()
#8  0x0806f657 in PDA::synchronizationTasks ()
#9  0x0807c413 in ThreadEventObject::customEvent ()
#10 0xb7071bc7 in QObject::event () from /usr/lib/libqt-mt.so.3
#11 0xb700bf80 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#12 0xb700c172 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#13 0xb77560cc in KApplication::notify () from /usr/lib/libkdecore.so.4
#14 0xb6f9cdb7 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#15 0xb700d4a3 in QApplication::sendPostedEvents ()
   from /usr/lib/libqt-mt.so.3
#16 0xb700d5aa in QApplication::sendPostedEvents ()
   from /usr/lib/libqt-mt.so.3
#17 0xb6faff4f in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#18 0xb7023cfb in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#19 0xb7023c1e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#20 0xb700ac13 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#21 0x080671a5 in main ()


---

### Post by bsander on 2006-04-18
I have the same problem :(

---

