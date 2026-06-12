---
title: "Kontact/Kmail and kde 3.5"
date: 2005-11-29
forum: Desktop Environments
---

### Post by wedge2k on 2005-11-29
I recently installed the kubuntu packages for kde 3.5.  While play'n around i tried opening up kontact and crashes immediately.  Here's what i get:

```
sanders@d-lnx005:~$ *** KMail got signal 11 (Crashing)
KCrash: Application 'kmail' crashing...
kontact
kmail: WARNING: [void KMFolderImap::setImapPath(const QString&)] ignoring empty path
kmail: WARNING: [void KMFolderImap::setImapPath(const QString&)] ignoring empty path
kmail: WARNING: [void KMFolderImap::setImapPath(const QString&)] ignoring empty path
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
sanders@d-lnx005:~$ *** KMail got signal 11 (Crashing)
KCrash: Application 'kontact' crashing...
```

It looks like its mostly Kmail thats crashing, any thoughts on what could be done?  Thanks!

Heres the debug info from the crash: 

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
[New Thread -1241459008 (LWP 32627)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#4  0xb555ded9 in KMFolder::noContent () from /usr/lib/libkmailprivate.so
#5  0xb55efa69 in KMAcctImap::processNewMail ()
   from /usr/lib/libkmailprivate.so
#6  0xb5591b0e in KMail::AccountManager::processNextCheck ()
   from /usr/lib/libkmailprivate.so
#7  0xb5591ccb in KMail::AccountManager::singleCheckMail ()
   from /usr/lib/libkmailprivate.so
#8  0xb5591e97 in KMail::AccountManager::checkMail ()
   from /usr/lib/libkmailprivate.so
#9  0xb56a94e6 in KMMainWidget::slotCheckMail ()
   from /usr/lib/libkmailprivate.so
#10 0xb56bebe8 in KMMainWidget::qt_invoke () from /usr/lib/libkmailprivate.so
#11 0xb703c929 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#12 0xb739be92 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#13 0xb705a344 in QSignal::activate () from /usr/lib/libqt-mt.so.3
#14 0xb7061e88 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#15 0xb6fd3f80 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#16 0xb6fd4172 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#17 0xb7696c3c in KApplication::notify () from /usr/lib/libkdecore.so.4
#18 0xb6f64db7 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#19 0xb6fc599b in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#20 0xb6f78a84 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#21 0xb6febcfb in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#22 0xb6febc1e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#23 0xb6fd2c13 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#24 0x0805aa4d in ?? ()
#25 0xbfe20fe0 in ?? ()
#26 0x00000001 in ?? ()
#27 0x00000001 in ?? ()
#28 0x00000000 in ?? ()
#29 0x00000015 in ?? ()
#30 0x0804ea9b in ?? ()
#31 0x00000008 in ?? ()
#32 0x00000004 in ?? ()
#33 0xb797ccd0 in ?? () from /usr/lib/libstdc++.so.6
#34 0xb786f908 in __malloc_initialize_hook ()
   from /lib/tls/i686/cmov/libc.so.6
#35 0x00000002 in ?? ()
#36 0x00000015 in ?? ()
#37 0x08065248 in vtable for QGList ()
#38 0xb7f0c160 in ?? ()
#39 0x080c1600 in ?? ()
#40 0x00000000 in ?? ()
#41 0x080c1260 in ?? ()
#42 0x08171eb0 in ?? ()
#43 0x081718f8 in ?? ()
#44 0x0818ecf0 in ?? ()
#45 0x00000000 in ?? ()
#46 0x00000000 in ?? ()
#47 0x00000001 in ?? ()
#48 0x08079a70 in ?? ()
#49 0x00000000 in ?? ()
#50 0x00000000 in ?? ()
#51 0x081974a8 in ?? ()
#52 0x080e1478 in ?? ()
#53 0x0815e8d0 in ?? ()
#54 0x08058700 in ?? ()
#55 0x080652cc in vtable for QGList ()
#56 0x0815fb90 in ?? ()
#57 0x0815f9f0 in ?? ()
#58 0x0817af78 in ?? ()
#59 0xb74cf4e0 in vtable for QCString () from /usr/lib/libqt-mt.so.3
#60 0x08078608 in ?? ()
#61 0xbfe210c4 in ?? ()
#62 0x0815f4b8 in ?? ()
#63 0x0807a368 in ?? ()
#64 0x00000121 in ?? ()
#65 0x000001ff in ?? ()
#66 0xb6da6ecc in ?? () from /usr/lib/libqt-mt.so.3
#67 0x00000000 in ?? ()
#68 0x0806d6a8 in ?? ()
#69 0x08058701 in ?? ()
#70 0x0819a488 in ?? ()
#71 0x08198008 in ?? ()
#72 0xb774f9fc in ?? () from /lib/tls/i686/cmov/libc.so.6
#73 0xb774732c in ?? () from /lib/tls/i686/cmov/libc.so.6
#74 0x08077340 in ?? ()
#75 0x00000049 in ?? ()
#76 0xb74b2460 in ?? () from /usr/lib/libqt-mt.so.3
#77 0x00000000 in ?? ()
#78 0xb7f22ca0 in _rtld_global () from /lib/ld-linux.so.2
#79 0xbfe210a8 in ?? ()
#80 0xb702cc5f in QAsciiDict<void>::insert () from /usr/lib/libqt-mt.so.3
#81 0xb7758ea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#82 0x08058561 in ?? ()

```

Let me know if that helps.


After further playing with, I want to say that its either the filters, or the bongo spam filter app that is causing the new kmail to crash.  Has anyone else had those same problems?

---

### Post by fimbulvetr on 2005-11-30
rm -rf /var/tmp/kdecache-*

---

### Post by Pietro Pizzi on 2005-12-02
Hi,

I have the same Problem but "rm .." don't helps. Any other suggestion?

Thanks,
Pietro Pizzi

---

### Post by armeck on 2005-12-02
Similar issue here, fresh install of Kubuntu 5.10, then straight to the KDE 3.5 upgrade.  I don;t get the same error message though: 

```
Library files for "libkmailpart.la" not found in paths.
```

Any guidance would be appreciated...

---

### Post by N6546R on 2005-12-02
Do another upgrade pass and install kmail. I believe I did three upgrades to get all the dependencies resolved for KDE3.5.

Perry

[QUOTE=armeck]Similar issue here, fresh install of Kubuntu 5.10, then straight to the KDE 3.5 upgrade.  I don;t get the same error message though: 

```
Library files for "libkmailpart.la" not found in paths.
```

Any guidance would be appreciated...[/QUOTE]

---

### Post by armeck on 2005-12-02
[QUOTE=N6546R]Do another upgrade pass and install kmail. I believe I did three upgrades to get all the dependencies resolved for KDE3.5.

Perry[/QUOTE]

I keep getting this message:

```
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  akregator kaddressbook karm kdepim-wizards knotes kontact korganizer
  libkpimexchange1 libkpimidentities1
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
```

Do I not have the proper repositories open?

---

### Post by vkapartz on 2005-12-04
I had exactly the same problem and I can confirm that it is one of missing repositories. I just edited /etc/apt/sources.list and uncommented all sources. After that all packages were upgraded successfully.

---

### Post by snowjunkie on 2006-01-09
[QUOTE=armeck]I keep getting this message:

```
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  akregator kaddressbook karm kdepim-wizards knotes kontact korganizer
  libkpimexchange1 libkpimidentities1
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
```

Do I not have the proper repositories open?[/QUOTE]

I simply stated them explicitly - for example 

sudo apt-get install kontact

etc.

---

### Post by mgimera on 2006-11-18
I've been having similar problems with Kontact/kmail - I'm on a fresh install of Ubuntu 6.06 LTS, and I update like crazy (e.g. when trying to apt-get kontact etc it tells me I've got the newest version) 
I ran from terminal to get this:

wombat@wombat-laptop:~$ kontact
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
wombat@wombat-laptop:~$ WeaverThreadLogger: thread (ID: 1) suspended.
WeaverThreadLogger: thread (ID: 2) suspended.
WeaverThreadLogger: thread (ID: 3) suspended.
WeaverThreadLogger: thread (ID: 4) suspended.
/bin/sh: bogofilter: command not found
/bin/sh: bogofilter: command not found
/bin/sh: bogofilter: command not found
/bin/sh: bogofilter: command not found
/bin/sh: bogofilter: command not found
/bin/sh: bogofilter: command not found
/bin/sh: bogofilter: command not found
/bin/sh: bogofilter: command not found
/bin/sh: bogofilter: command not found
/bin/sh: bogofilter: command not found
/bin/sh: bogofilter: command not found
QWidget::setMaximumSize: (unnamed/RecipientComboBox) The largest allowed size is (32767,32767) **THIS IS WHERE IT FROZE**

wombat@wombat-laptop:~$ *** KMail got signal 15 (Exiting) **THIS IS WHERE I KILLED IT**

Help is much appreciated

---

