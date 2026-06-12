---
title: "Like my new Wallpaper?"
date: 2005-04-08
forum: Desktop Environments
---

### Post by denzilla on 2005-04-08
Hey guys! I thought I would share my new wallpaper with ya. Its kinda tacky, but I figured that since the message is displayed too me every 5min, it must really want to be part of my desktop. 

Sorry for being a smartass, but I'm about to lose my mind over this stupid error! I would give my left testicle in exchange for this damn error to go away forever. Always a sig11 error with the same backtrace. Always happens browsing file and starting apps. Got a Geforce ti4600 in box now, so its not an ATI problem. The one Linux distro I fell I can stick with and this.... ](*,)

---

### Post by Jujimufu on 2005-04-08
HAHAHAHA! That's excellent! Bravo!

---

### Post by telmo on 2005-04-09
Rofl!

---

### Post by bored2k on 2005-04-09
This is quite a problem when we have over 500 unanswered threads. Do you actually think there are more people interested in one of the thousands of wallpapers we display than helping another person in need. Should I know a solution, what tells me I should even click to help.

(then people whine about the forums not being friendly enough)

P.S. - I excuse myself, the fun bored2k is in his bed already.

---

### Post by denzilla on 2005-04-09
I'm not sure how to take that response  :-s I'm really asking for help, but since this error is humbling even the mightiest Linux user, I'm injecting some humor into the situation to calm myselff down. It just frustrates me that I like Kubuntu so much and can't really get much use out of it beyond toying with it due to this one stupid error.

---

### Post by bored2k on 2005-04-09
Have you filed a bug report ? or checked if it has been adressed before?

---

### Post by denzilla on 2005-04-09
Yea, I filed a bug report, but the response was... " Is your cpu overheating?". I just checked the status of the bug and nothing indicated yet. The cpu isn't overheating, btw.

---

### Post by dermotti on 2005-04-09
I didnt have this issue when i was runnig Kubuntu via apt get in uubuntu. I install Kubuntu straight off the disk and im getting this error like crazy

---

### Post by denzilla on 2005-04-09
Nice to see I have a friend in my own personal hell :)

---

### Post by roachk71 on 2005-04-09
Arrrgghh!!  ](*,) 

I reported this to KDE.org a couple of weeks ago, and so far there's been no resolution to the problem... It's always (11) SigSegV, and usually happens after launching Konqueror every other time, as well!

All I can say is that KDE and its apps have always been resource-intensive, and this problem will probably never go away... 256MB of RAM, and KDE and Konqueror still blowing up with memory bottlenecks and inefficient code... Hmmm... This bottleneck has been present since early versions of KDE...

 :roll:

I'll bet most of us are in this boat.

---

### Post by denzilla on 2005-04-09
Its a shame, really. I got to have some eye candy and KDE is beautiful when it runs right. Gnome just makes me want to go to sleep, doesn't matter what Gnome desktop I see. This crash and the duplicate hidden file glitch are the only two real problems I have with Kubuntu.

If one can install regular Ubuntu and KDE on top and not have issues, then there must be some glitch in the pure Kubuntu code.

---

### Post by jdong on 2005-04-09
Can we take a look at the backtrace?

---

### Post by digby on 2005-04-09
I have KDE installed via apt-get from Ubuntu, and I do see this problem, though not frequently.  I will try to remembert to backtrace it next time it pops up.

---

### Post by denzilla on 2005-04-09
[QUOTE=jdong]Can we take a look at the backtrace?[/QUOTE]

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
[Thread debugging using libthread_db enabled]
[New Thread -1229691488 (LWP 6318)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#4 0xb7c72843 in QMap<KIO::ListJob*, KDirLister::KDirListerPrivate::JobData>::insert () from /usr/lib/libkio.so.4
#5 0xb7c40ee0 in KDirLister::jobStarted () from /usr/lib/libkio.so.4
#6 0xb7c3a829 in KDirListerCache::updateDirectory ()
from /usr/lib/libkio.so.4
#7 0xb7c3bc72 in KDirListerCache::slotFileDirty () from /usr/lib/libkio.so.4
#8 0xb7c4232c in KDirListerCache::qt_invoke () from /usr/lib/libkio.so.4
#9 0xb73e6fdd in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#10 0xb73e74c4 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#11 0xb7bf80c4 in KDirWatch::dirty () from /usr/lib/libkio.so.4
#12 0xb7bf7ee3 in KDirWatch::setDirty () from /usr/lib/libkio.so.4
#13 0xb7bf62eb in KDirWatchPrivate::emitEvent () from /usr/lib/libkio.so.4
#14 0xb7bf6568 in KDirWatchPrivate::slotRescan () from /usr/lib/libkio.so.4
#15 0xb7bf84a5 in KDirWatchPrivate::qt_invoke () from /usr/lib/libkio.so.4
#16 0xb73e7067 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#17 0xb73e6eae in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#18 0xb770419d in QTimer::timeout () from /usr/lib/libqt-mt.so.3
#19 0xb7406c05 in QTimer::event () from /usr/lib/libqt-mt.so.3
#20 0xb738f370 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#21 0xb738e9d4 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#22 0xb78df960 in KApplication::notify () from /usr/lib/libkdecore.so.4
#23 0xb737f858 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#24 0xb733b95f in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#25 0xb73a074c in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#26 0xb73a060e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#27 0xb738f57b in QApplication::exec () from /usr/lib/libqt-mt.so.3
#28 0xb694c06d in kdemain () from /usr/lib/libkdeinit_konqueror.so
#29 0xb7fe7776 in kdeinitmain () from /usr/lib/kde3/konqueror.so
#30 0x0804cb6e in ?? ()
#31 0x00000004 in ?? ()
#32 0x081357a8 in ?? ()
#33 0x00000001 in ?? ()
#34 0x00000000 in ?? ()
#35 0x00000000 in ?? ()
#36 0x00000000 in ?? ()
#37 0x00001f80 in ?? ()
#38 0x00000000 in ?? ()
#39 0x00000000 in ?? ()
#40 0x10000000 in ?? ()
#41 0x00000000 in ?? ()
#42 0x00001000 in ?? ()
#43 0x00000000 in ?? ()
#44 0x00000000 in ?? ()
#45 0x01000000 in ?? ()
#46 0x00000000 in ?? ()
#47 0x00000000 in ?? ()
#48 0x00000000 in ?? ()
#49 0x00000000 in ?? ()
#50 0x00000000 in ?? ()
#51 0x00000000 in ?? ()
#52 0x00000000 in ?? ()
#53 0x00000000 in ?? ()
#54 0x00000000 in ?? ()
#55 0x08136640 in ?? ()
#56 0x00000000 in ?? ()
#57 0x00000000 in ?? ()
#58 0x00000000 in ?? ()
#59 0x00000000 in ?? ()
#60 0x00000000 in ?? ()
#61 0x00000000 in ?? ()
#62 0x00000000 in ?? ()
#63 0xb7805ee0 in vtable for QGArray () from /usr/lib/libqt-mt.so.3
#64 0x00000000 in ?? ()
#65 0x08135d68 in ?? ()
#66 0xb7eaf9e0 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#67 0xbffff710 in ?? ()
#68 0x00000000 in ?? ()
#69 0x00000000 in ?? ()
#70 0x00000018 in ?? ()
#71 0xb7806228 in vtable for QPtrCollection () from /usr/lib/libqt-mt.so.3
#72 0x00000001 in ?? ()
#73 0x00000000 in ?? ()
#74 0x00000000 in ?? ()
#75 0x00000000 in ?? ()
#76 0xffffffff in ?? ()
#77 0x00000000 in ?? ()
#78 0x00000000 in ?? ()
#79 0xb7df4b01 in malloc () from /lib/tls/i686/cmov/libc.so.6
#80 0x0804e046 in ?? ()
#81 0x00000004 in ?? ()
#82 0x08136114 in ?? ()
#83 0x0813614d in ?? ()
#84 0x0813614d in ?? ()
#85 0x0000001a in ?? ()
#86 0x081364c9 in ?? ()
#87 0x00000001 in ?? ()
#88 0x00000000 in ?? ()
#89 0x00000000 in ?? ()
#90 0x081364cd in ?? ()
#91 0x00000000 in ?? ()
#92 0x00000000 in ?? ()
#93 0x00000000 in ?? ()
#94 0x00000000 in ?? ()
#95 0x00000000 in ?? ()
#96 0x00000000 in ?? ()
#97 0x00000000 in ?? ()
#98 0x081364cd in ?? ()
#99 0x00000000 in ?? ()
#100 0x00000000 in ?? ()
#101 0x0813615a in ?? ()
#102 0x0000001a in ?? ()
#103 0x0813614d in ?? ()
#104 0x0813611e in ?? ()
#105 0x08136114 in ?? ()
#106 0x00000004 in ?? ()
#107 0x08136110 in ?? ()
#108 0x00000000 in ?? ()
#109 0x00000000 in ?? ()
#110 0x00000000 in ?? ()
#111 0x00000006 in ?? ()
#112 0x000003e5 in ?? ()
#113 0x080513d8 in vtable for QCString ()
#114 0x080a7f18 in ?? ()
#115 0x00000000 in ?? ()
#116 0x00000000 in ?? ()
#117 0x080513d8 in vtable for QCString ()
#118 0x08135d18 in ?? ()
#119 0xb7dad03b in ssignal () from /lib/tls/i686/cmov/libc.so.6
#120 0x0804e66e in ?? ()
#121 0x00000004 in ?? ()
#122 0xbffff950 in ?? ()
#123 0xbffff8d4 in ?? ()
#124 0xbffff9c0 in ?? ()
#125 0x00000000 in ?? ()
#126 0xbffff960 in ?? ()
#127 0xbffff8c8 in ?? ()
#128 0xb7f6fd13 in operator delete () from /usr/lib/libstdc++.so.5
#129 0x0804f5cc in ?? ()
#130 0x00000000 in ?? ()
#131 0xbffffbbe in ?? ()
#132 0x00000001 in ?? ()
#133 0x00000000 in ?? ()
#134 0x00000000 in ?? ()
#135 0x00000000 in ?? ()
#136 0x00000000 in ?? ()
#137 0x00000000 in ?? ()
#138 0x00000000 in ?? ()
#139 0x080502b6 in _IO_stdin_used ()
#140 0x00000000 in ?? ()
#141 0xbffffb98 in ?? ()
#142 0xb7daf980 in __cxa_atexit () from /lib/tls/i686/cmov/libc.so.6
#143 0xb7d9a8c8 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#144 0x0804b581 in ?? ()

```

---

### Post by dermotti on 2005-04-09
Ya know that looks almost exactly the same as my backtrace

---

### Post by denzilla on 2005-04-09
From what I see, its the same backtrace everytime KDE crashes. I submitted the duplicate hidden file bug and this particular bug separately and they rejected the duplicate files bug because they said it was the same backtrace has the bug we're talking about here.

---

### Post by dermotti on 2005-04-10
I can confirm i get the same exact error. :-( help!

---

