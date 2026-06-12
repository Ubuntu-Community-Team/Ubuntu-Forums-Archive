---
title: "Kopete crash on attempt to login to msn/hotmail on gutsy."
date: 2007-10-17
forum: Desktop Environments
---

### Post by pyrrhicvictory on 2007-10-17
When attempting to login to hotmail/msn using kopete, It crashes miserably, and even when not 

[Thread debugging using libthread_db enabled]
[New Thread 47221821488176 (LWP 7557)]
[KCrash handler]
#5  0x00002af2bae0ab53 in MSNAccount::slotNotifySocketClosed ()
   from /usr/lib/libkopete_msn_shared.so.0
#6  0x00002af2bae1262c in MSNAccount::qt_invoke ()
   from /usr/lib/libkopete_msn_shared.so.0
#7  0x00002af2ab9dfd76 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#8  0x00002af2ab9e0910 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#9  0x00002af2bae2d26a in MSNNotifySocket::disconnect ()
   from /usr/lib/libkopete_msn_shared.so.0
#10 0x00002af2bae2f87c in MSNNotifySocket::qt_invoke ()
   from /usr/lib/libkopete_msn_shared.so.0
#11 0x00002af2ab9dfd76 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#12 0x00002af2ab9e0910 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#13 0x00002af2bae46d93 in MSNSecureLoginHandler::slotTweenerReceived ()
   from /usr/lib/libkopete_msn_shared.so.0
#14 0x00002af2bae47dc0 in MSNSecureLoginHandler::qt_invoke ()
   from /usr/lib/libkopete_msn_shared.so.0
#15 0x00002af2ab9dfd76 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#16 0x00002af2a91a1152 in KIO::Job::result () from /usr/lib/libkio.so.4
#17 0x00002af2a91ed2d1 in KIO::Job::emitResult () from /usr/lib/libkio.so.4
#18 0x00002af2a91ed73a in KIO::SimpleJob::slotFinished ()
   from /usr/lib/libkio.so.4
#19 0x00002af2a91edd8a in KIO::TransferJob::slotFinished ()
   from /usr/lib/libkio.so.4
#20 0x00002af2a91ecd58 in KIO::SimpleJob::qt_invoke ()
   from /usr/lib/libkio.so.4
#21 0x00002af2a91ecdbd in KIO::TransferJob::qt_invoke ()
   from /usr/lib/libkio.so.4
#22 0x00002af2ab9dfd76 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#23 0x00002af2abd4de51 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#24 0x00002af2ab9feeeb in QSignal::activate () from /usr/lib/libqt-mt.so.3
#25 0x00002af2aba05f1e in QSingleShotTimer::event ()
   from /usr/lib/libqt-mt.so.3
#26 0x00002af2ab97b2a2 in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#27 0x00002af2ab97d031 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#28 0x00002af2aa602248 in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#29 0x00002af2ab90dd12 in QApplication::sendEvent ()
   from /usr/lib/libqt-mt.so.3
#30 0x00002af2ab96e55c in QEventLoop::activateTimers ()
   from /usr/lib/libqt-mt.so.3
#31 0x00002af2ab922443 in QEventLoop::processEvents ()
   from /usr/lib/libqt-mt.so.3
#32 0x00002af2ab9947e7 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#33 0x00002af2ab9945ef in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#34 0x00002af2ab97cd68 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#35 0x000000000044091a in ?? ()
#36 0x00002af2af2e1b44 in __libc_start_main () from /lib/libc.so.6
#37 0x0000000000431639 in ?? ()
#38 0x00007fff03f08798 in ?? ()
#39 0x0000000000000000 in ?? ()

This is on kde 3.5.8 gutsy 64 bit.

---

### Post by kugn on 2007-10-17
I'm experiencing that too. and i'm on a ppc.

---

### Post by pyrrhicvictory on 2007-10-17
I am glad to see that I am not the only one going through this. For a minute there, I thought I was going insane.

---

### Post by kugn on 2007-10-18
There is a parallel thread [here]("http://ubuntuforums.org/showthread.php?t=577996"), with a fix :)

---

### Post by bubbalouie on 2007-10-18
Cheers :)

---

### Post by philinux on 2007-10-18
That .deb update fixed mine too

---

### Post by m0ns00n on 2007-10-19
I don't see the amd64 deb. Is there a fix for amd64 too? :-)

---

### Post by SalsaDoom on 2007-10-22
Yup, I think its probably safe to say just about everyone is gonna hit this one. It'd be nice to see an update to fix it, this is all pretty annoying stuff. Same story on AMD64. 

--SD

---

