---
title: "KDE 3.4.1: KDE Panel (Kicker) crashed when logout"
date: 2005-06-17
forum: Desktop Environments
---

### Post by oobuntoo on 2005-06-17
Has any one experienced KDE Panel (kicker) crashing problem when logging out of KDE? I kept getting this problem after upgrading to KDE 3.4.1. I think this is a KDE bug. I'll look around to see if any one has submit a bug report similar to this. Here is a backtrace from the crash handler:

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
[Thread debugging using libthread_db enabled]
[New Thread -1229949536 (LWP 7430)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#4  0x00000000 in ?? ()
#5  0xb74f7eea in QPtrList<QPopupMenu>::deleteItem ()
   from /usr/lib/libqt-mt.so.3
#6  0xb76565cc in QGList::clear () from /usr/lib/libqt-mt.so.3
#7  0xb695ee2e in PanelServiceMenu::~PanelServiceMenu ()
   from /usr/lib/libkdeinit_kicker.so
#8  0xb695a682 in PanelKMenu::~PanelKMenu ()
   from /usr/lib/libkdeinit_kicker.so
#9  0xb692f3fe in MenuManager::~MenuManager ()
   from /usr/lib/libkdeinit_kicker.so
#10 0xb73b9051 in QObject::~QObject () from /usr/lib/libqt-mt.so.3
#11 0xb7360581 in QApplication::~QApplication () from /usr/lib/libqt-mt.so.3
#12 0xb78ba299 in KApplication::~KApplication () from /usr/lib/libkdecore.so.4
#13 0xb795e287 in KUniqueApplication::~KUniqueApplication ()
   from /usr/lib/libkdecore.so.4
#14 0xb69159b9 in Kicker::~Kicker () from /usr/lib/libkdeinit_kicker.so
#15 0xb6913903 in kdemain () from /usr/lib/libkdeinit_kicker.so
#16 0xb699f776 in kdeinitmain () from /usr/lib/kde3/kicker.so
#17 0x0804cbd2 in ?? ()
#18 0x00000001 in ?? ()
#19 0x081361f8 in ?? ()
#20 0x00000001 in ?? ()
#21 0x00000000 in ?? ()
#22 0x00000000 in ?? ()
#23 0x00000000 in ?? ()
#24 0x00000000 in ?? ()
#25 0x00000000 in ?? ()
#26 0x00000000 in ?? ()
#27 0x00000000 in ?? ()
#28 0x00000000 in ?? ()
#29 0x00000000 in ?? ()
#30 0x00000000 in ?? ()
#31 0x00000000 in ?? ()
#32 0x00000000 in ?? ()
#33 0x00000000 in ?? ()
#34 0x00000000 in ?? ()
#35 0x00000000 in ?? ()
#36 0x00000000 in ?? ()
#37 0x00000000 in ?? ()
#38 0x00000000 in ?? ()
#39 0x00000000 in ?? ()
#40 0x00000000 in ?? ()
#41 0x00000000 in ?? ()
#42 0x081366c8 in ?? ()
#43 0x00000000 in ?? ()
#44 0x00000000 in ?? ()
#45 0x00000000 in ?? ()
#46 0x00000000 in ?? ()
#47 0x00000000 in ?? ()
#48 0x00000000 in ?? ()
#49 0x00000000 in ?? ()
#50 0xb77daee0 in vtable for QGArray () from /usr/lib/libqt-mt.so.3
#51 0x00000000 in ?? ()
#52 0x00004010 in ?? ()
#53 0x00000000 in ?? ()
#54 0x00000000 in ?? ()
#55 0x00000000 in ?? ()
#56 0x00000000 in ?? ()
#57 0x00000000 in ?? ()
#58 0x0805a548 in ?? ()
#59 0x00000000 in ?? ()
#60 0x00000010 in ?? ()
#61 0xb7ea89e0 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#62 0xb7ea8038 in ?? () from /lib/tls/i686/cmov/libc.so.6
#63 0xb7ea89e0 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#64 0x00000001 in ?? ()
#65 0xbffff738 in ?? ()
#66 0xb7dedb0b in malloc () from /lib/tls/i686/cmov/libc.so.6
#67 0x0804e0fb in ?? ()
#68 0x00000001 in ?? ()
#69 0x08135b54 in ?? ()
#70 0x08135b5b in ?? ()
#71 0x00000000 in ?? ()
#72 0x00000000 in ?? ()
#73 0x08135b5f in ?? ()
#74 0x00000000 in ?? ()
#75 0x00000000 in ?? ()
#76 0x00000000 in ?? ()
#77 0x08050457 in _IO_stdin_used ()
#78 0x00000000 in ?? ()
#79 0x00000000 in ?? ()
#80 0x00000000 in ?? ()
#81 0x08050457 in _IO_stdin_used ()
#82 0x00000000 in ?? ()
#83 0x00000000 in ?? ()
#84 0x08135b5f in ?? ()
#85 0x00000000 in ?? ()
#86 0x00000000 in ?? ()
#87 0x08135b5b in ?? ()
#88 0x08135b54 in ?? ()
#89 0x00000001 in ?? ()
#90 0x08135b50 in ?? ()
#91 0x00000000 in ?? ()
#92 0x00000000 in ?? ()
#93 0x00000000 in ?? ()
#94 0x0000000c in ?? ()
#95 0x00000013 in ?? ()
#96 0x080513d8 in vtable for QCString ()
#97 0x0805a550 in ?? ()
#98 0x00000000 in ?? ()
#99 0x00000000 in ?? ()
#100 0x080513d8 in vtable for QCString ()
#101 0x0805a540 in ?? ()
#102 0x80cd0000 in ?? ()
#103 0x00000000 in ?? ()
#104 0xbffffb38 in ?? ()
#105 0xbffffa20 in ?? ()
#106 0xbffffaa0 in ?? ()
#107 0x00000001 in ?? ()
#108 0xbffffa20 in ?? ()
#109 0x00001ced in ?? ()
#110 0xbffffb38 in ?? ()
#111 0x0804e61e in ?? ()
#112 0x00000008 in ?? ()
#113 0xbffffaa0 in ?? ()
#114 0xbffffa20 in ?? ()
#115 0xbffff9a0 in ?? ()
#116 0x00000000 in ?? ()
#117 0xbffff940 in ?? ()
#118 0xbffff8a8 in ?? ()
#119 0xb7f68d13 in operator delete () from /usr/lib/libstdc++.so.5

---

### Post by kastorff on 2005-06-17
> **oobuntoo]Has any one experienced KDE Panel (kicker) crashing problem when logging out of KDE? I kept getting this problem after upgrading to KDE 3.4.1. I think this is a KDE bug. I'll look around to see if any one has submit it a bug report similar to this. Here is a backtrace from the crash handler:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared said:**
> 
#117 0xbffff940 in ?? ()
#118 0xbffff8a8 in ?? ()
#119 0xb7f68d13 in operator delete () from /usr/lib/libstdc++.so.5
 I've seen reports of this on various distros, so I think you're on the right track thinking it's a KDE bug and not Ubuntu specific. One suggestion I've seen is to disable running programs in the system tray and enable them one by one to check for the issue. Course that would be a bit of a pain since you have to logout each time...

---

### Post by abandoned_hussam on 2005-06-18
I seem to be having the same problem on KDE 3.4.1

---

### Post by oobuntoo on 2005-06-18
I did some googling and found that someone had submitted a bug report that reflects this problem. You can check it out [here](http://bugs.kde.org/show_bug.cgi?id=106922)

---

### Post by z-vet on 2005-06-18
I have this problem too. KDE bug and not Kubuntu, imho.

---

### Post by abandoned_hussam on 2005-06-20
I hope it gets fixed in kde 3.4.2

---

