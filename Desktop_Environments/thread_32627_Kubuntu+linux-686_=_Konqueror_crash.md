---
title: "Kubuntu+linux-686 = Konqueror crash?"
date: 2005-05-08
forum: Desktop Environments
---

### Post by vannguyen0 on 2005-05-08
Hi,

I've installed the base installation of Ubuntu.
Then I installed linux-686.
Then I installed kubuntu-desktop.

Now Konqueror crashes.  Here's the output from the KDE crash handler:

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
[New Thread -1229703776 (LWP 8618)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#4  0xb7c6f843 in QMap<KIO::ListJob*, KDirLister::KDirListerPrivate::JobData>::insert () from /usr/lib/libkio.so.4
#5  0xb7c3dee0 in KDirLister::jobStarted () from /usr/lib/libkio.so.4
#6  0xb7c37829 in KDirListerCache::updateDirectory ()
   from /usr/lib/libkio.so.4
#7  0xb7c38c72 in KDirListerCache::slotFileDirty () from /usr/lib/libkio.so.4
#8  0xb7c3f32c in KDirListerCache::qt_invoke () from /usr/lib/libkio.so.4
#9  0xb73e3fdd in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#10 0xb73e44c4 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#11 0xb7bf50c4 in KDirWatch::dirty () from /usr/lib/libkio.so.4
#12 0xb7bf4ee3 in KDirWatch::setDirty () from /usr/lib/libkio.so.4
#13 0xb7bf32eb in KDirWatchPrivate::emitEvent () from /usr/lib/libkio.so.4
#14 0xb7bf3568 in KDirWatchPrivate::slotRescan () from /usr/lib/libkio.so.4
#15 0xb7bf54a5 in KDirWatchPrivate::qt_invoke () from /usr/lib/libkio.so.4
#16 0xb73e4067 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#17 0xb73e3eae in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#18 0xb770119d in QTimer::timeout () from /usr/lib/libqt-mt.so.3
#19 0xb7403c05 in QTimer::event () from /usr/lib/libqt-mt.so.3
#20 0xb738c370 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#21 0xb738b9d4 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#22 0xb78dc960 in KApplication::notify () from /usr/lib/libkdecore.so.4
#23 0xb737c858 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#24 0xb733895f in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#25 0xb739d74c in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#26 0xb739d60e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#27 0xb738c57b in QApplication::exec () from /usr/lib/libqt-mt.so.3
#28 0xb694606d in kdemain () from /usr/lib/libkdeinit_konqueror.so
#29 0xb7fe7776 in kdeinitmain () from /usr/lib/kde3/konqueror.so
#30 0x0804cb6e in ?? ()
#31 0x00000003 in ?? ()
#32 0x081361f8 in ?? ()
#33 0x00000001 in ?? ()
#34 0x00000000 in ?? ()
#35 0x00000000 in ?? ()
#36 0x0000007b in ?? ()
#37 0x00001f80 in ?? ()
#38 0x0000ffff in ?? ()
#39 0x00000000 in ?? ()
#40 0x00000000 in ?? ()
#41 0x00000000 in ?? ()
#42 0x00000000 in ?? ()
#43 0x00000000 in ?? ()
#44 0x00000000 in ?? ()
#45 0x00000000 in ?? ()
#46 0x00000000 in ?? ()
#47 0x00000000 in ?? ()
#48 0x00000000 in ?? ()
#49 0x00000000 in ?? ()
#50 0x00000000 in ?? ()
#51 0x00000000 in ?? ()
#52 0x00000000 in ?? ()
#53 0x00000000 in ?? ()
#54 0x00000000 in ?? ()
#55 0x08136210 in ?? ()
#56 0x00000000 in ?? ()
#57 0x00000000 in ?? ()
#58 0x00000000 in ?? ()
#59 0x00000000 in ?? ()
#60 0x00000000 in ?? ()
#61 0x00000000 in ?? ()
#62 0x00000000 in ?? ()
#63 0xb7802ee0 in vtable for QGArray () from /usr/lib/libqt-mt.so.3
#64 0x00000000 in ?? ()
#65 0x00000000 in ?? ()
#66 0x00000000 in ?? ()
#67 0x00000000 in ?? ()
#68 0x80000000 in ?? ()
#69 0x00004010 in ?? ()
#70 0x00000000 in ?? ()
#71 0x08135fb0 in ?? ()
#72 0x00000000 in ?? ()
#73 0x00000010 in ?? ()
#74 0xb7eac9e0 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#75 0xb7eac038 in ?? () from /lib/tls/i686/cmov/libc.so.6
#76 0xb7eac9e0 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#77 0x00000001 in ?? ()
#78 0xbffff738 in ?? ()
#79 0xb7df1b0b in malloc () from /lib/tls/i686/cmov/libc.so.6
#80 0x0804e046 in ?? ()
#81 0x00000003 in ?? ()
#82 0x08135d6c in ?? ()
#83 0x08135db9 in ?? ()
#84 0x00000000 in ?? ()
#85 0x00000000 in ?? ()
#86 0x08135dbd in ?? ()
#87 0x00000000 in ?? ()
#88 0x00000000 in ?? ()
#89 0x00000000 in ?? ()
#90 0x080502b6 in _IO_stdin_used ()
#91 0x00000000 in ?? ()
#92 0x00000000 in ?? ()
#93 0x00000000 in ?? ()
#94 0x00000000 in ?? ()
#95 0x00000000 in ?? ()
#96 0x00000000 in ?? ()
#97 0x00000000 in ?? ()
#98 0x080502b6 in _IO_stdin_used ()
#99 0x00000000 in ?? ()
#100 0x00000000 in ?? ()
#101 0x08135dbd in ?? ()
#102 0x00000000 in ?? ()
#103 0x00000000 in ?? ()
#104 0x08135d76 in ?? ()
#105 0x08135d6c in ?? ()
#106 0x00000003 in ?? ()
#107 0x08135d68 in ?? ()
#108 0x000021a7 in ?? ()
#109 0x00000004 in ?? ()
#110 0x00000004 in ?? ()
#111 0x0000000c in ?? ()
#112 0x00000059 in ?? ()
#113 0x080513d8 in vtable for QCString ()
#114 0x08135fb8 in ?? ()
#115 0x00000000 in ?? ()
#116 0x00000000 in ?? ()
#117 0x080513d8 in vtable for QCString ()
#118 0x081358d8 in ?? ()
#119 0x80cd0000 in ?? ()
#120 0x00000000 in ?? ()
#121 0xbffffb48 in ?? ()
#122 0xbffffa30 in ?? ()
#123 0xbffffab0 in ?? ()
#124 0x00000001 in ?? ()
#125 0xbffffa30 in ?? ()
#126 0x0000217a in ?? ()
#127 0xbffffb48 in ?? ()
#128 0x0804e591 in ?? ()
#129 0x00000008 in ?? ()
#130 0xbffffab0 in ?? ()
#131 0xbffffa30 in ?? ()
#132 0xbffff9b0 in ?? ()
#133 0x00000000 in ?? ()
#134 0xbffff950 in ?? ()
#135 0xbffff8b8 in ?? ()
#136 0xb7f6cd13 in operator delete () from /usr/lib/libstdc++.so.5


Any Ideas?

---

### Post by David R on 2005-05-09
This is a well known problem, and I don't think it has something to see with linux-686.
You must have the duplicate icons bug too, haven't you ?

There is a topic about these problems : [http://www.ubuntuforums.org/showthread.php?t=26043](http://www.ubuntuforums.org/showthread.php?t=26043)

---

