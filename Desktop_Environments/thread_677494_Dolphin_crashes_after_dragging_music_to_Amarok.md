---
title: "Dolphin crashes after dragging music to Amarok"
date: 2008-01-24
forum: Desktop Environments
---

### Post by tutwabee on 2008-01-24
Sometimes I play music that is not yet in my collection.  I play it by dragging files from Dolphin to Amarok.  It drags in fine and plays fine but afterwards Dolphin will almost always crash within 2 seconds.  This is the crash error I get:

> 
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
[Thread debugging using libthread_db enabled]
[New Thread -1234209088 (LWP 25777)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#6  0x00000000 in ?? ()
#7  0xb6f3aaf0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#8  0xb6f3c91f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#9  0xb7700ca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#10 0xb6ecd209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#11 0xb6f3b2bb in qt_dispatchEnterLeave () from /usr/lib/libqt-mt.so.3
#12 0xb6eca3b2 in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#13 0xb6ee11a4 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#14 0xb6f551ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#15 0xb6f54fde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#16 0xb6f3c699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#17 0x08092586 in ?? ()
#18 0xbfcb1398 in ?? ()
#19 0x00000001 in ?? ()
#20 0x00000001 in ?? ()
#21 0x00000000 in ?? ()


---

### Post by tutwabee on 2008-05-13
Update: I am using Hardy Heron now and I still have this problem.

---

