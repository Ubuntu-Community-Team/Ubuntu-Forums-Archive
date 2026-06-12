---
title: "Problem w/ Kopete"
date: 2008-03-03
forum: Dell  Ubuntu Support
---

### Post by yaxomoxay on 2008-03-03
Everytime I try to log in to MSN using Kopete it crashes. I tried to uninstall it and reinstall it, I updated the system etc. I'm using a Dell Inspiron 1420 w/ Kubuntu. 
I get the following error :

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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1242072592 (LWP 11221)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#6  0xb59f711a in MSNAccount::slotNotifySocketClosed ()
   from /usr/lib/libkopete_msn_shared.so.0
#7  0xb59ff668 in MSNAccount::qt_invoke ()
   from /usr/lib/libkopete_msn_shared.so.0
#8  0xb6817893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#9  0xb6818338 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#10 0xb5a088dc in MSNSocket::socketClosed ()
   from /usr/lib/libkopete_msn_shared.so.0
#11 0xb5a1c4cd in MSNNotifySocket::disconnect ()
   from /usr/lib/libkopete_msn_shared.so.0
#12 0xb5a18f3b in MSNNotifySocket::sslLoginFailed ()
   from /usr/lib/libkopete_msn_shared.so.0
#13 0xb5a1f0f5 in MSNNotifySocket::qt_invoke ()
   from /usr/lib/libkopete_msn_shared.so.0
#14 0xb6817893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#15 0xb6818338 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#16 0xb5a3916c in MSNSecureLoginHandler::loginFailed ()
   from /usr/lib/libkopete_msn_shared.so.0
#17 0xb5a3940f in MSNSecureLoginHandler::slotTweenerReceived ()
   from /usr/lib/libkopete_msn_shared.so.0
#18 0xb5a3a5a6 in MSNSecureLoginHandler::qt_invoke ()
   from /usr/lib/libkopete_msn_shared.so.0
#19 0xb6817893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#20 0xb7452021 in KIO::Job::result () from /usr/lib/libkio.so.4
#21 0xb74aa8cd in KIO::Job::emitResult () from /usr/lib/libkio.so.4
#22 0xb74aad2e in KIO::SimpleJob::slotFinished () from /usr/lib/libkio.so.4
#23 0xb74ab43d in KIO::TransferJob::slotFinished () from /usr/lib/libkio.so.4
#24 0xb74aa301 in KIO::SimpleJob::qt_invoke () from /usr/lib/libkio.so.4
#25 0xb74aa363 in KIO::TransferJob::qt_invoke () from /usr/lib/libkio.so.4
#26 0xb6817893 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#27 0xb6ba38ec in QSignal::signal () from /usr/lib/libqt-mt.so.3
#28 0xb6837842 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#29 0xb683f258 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#30 0xb67aeaf0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#31 0xb67b091f in QApplication::notify () from /usr/lib/libqt-mt.so.3
#32 0xb6f74ca2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#33 0xb6741209 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#34 0xb67a153b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#35 0xb6755d49 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#36 0xb67c91ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#37 0xb67c8fde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#38 0xb67b0699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#39 0x0807f95c in ?? ()
#40 0xbff34914 in ?? ()
#41 0xbff3490c in ?? ()
#42 0xbff34904 in ?? ()
#43 0x00000000 in ?? ()



ThANKS !

---

### Post by yaxomoxay on 2008-03-04
no one ? I really need kopete and I don't know how to fix this problem !!

---

### Post by yaxomoxay on 2008-03-05
I found a solution here, in case anyone in the future will need it :

[https://bugs.launchpad.net/ubuntu/+source/kopete/+bug/149263](https://bugs.launchpad.net/ubuntu/+source/kopete/+bug/149263)

---

