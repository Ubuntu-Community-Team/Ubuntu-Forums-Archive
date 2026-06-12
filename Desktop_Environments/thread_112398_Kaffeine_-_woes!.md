---
title: "Kaffeine - woes!"
date: 2006-01-04
forum: Desktop Environments
---

### Post by mpierce on 2006-01-04
Kaffeine is refusing to play. Crashing with every launch when trying to play a vcd/svcd or dvd (mplayer is working fine as is vlc).

When launched, konqueror will launch and tell me:
An error occurred while loading media:/hdc:
The file or folder media:/hdc does not exist.

/media/hdc is the default in fstab for cdrom0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/dvd is linked to /dev/hdc

The crash is the usual kde crash message:
Kaffeine player crashed and caused a signal 8

Pkgs installed are and debug info show below this:
mpierce@mother:~$ dpkg -l | grep kaffeine
ii  kaffeine                                            0.7.1-1.3ubuntu1~breezy1             versatile media player for KDE 3
ii  kaffeine-gstreamer                                  0.7.1-1.3ubuntu1~breezy1             GStreamer engine for kaffeine media player
ii  kaffeine-mozilla                                    0.4.3.1-1                            mozilla plugin that lanches kaffeine for sup
ii  kaffeine-xine                                       0.7.1-1.3ubuntu1~breezy1             Xine engine for kaffeine media player

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1231767872 (LWP 27779)]
[New Thread -1246667856 (LWP 27991)]
[New Thread -1240470608 (LWP 27781)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6bc52ce in __lll_mutex_lock_wait ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6bc1fdb in _L_mutex_lock_33 () from /lib/tls/i686/cmov/libpthread.so.0
#3  0xb7f8f711 in _dl_rtld_di_serinfo () from /lib/ld-linux.so.2
#4  0xb6c350bb in _XLockDisplay (dpy=0x813ac58) at ../../src/locking.c:481
#5  0xb6c2b025 in XFreeCursor (dpy=0x813ac58, cursor=4294967292)
    at ../../src/FreeCurs.c:40
#6  0xb707915b in QCursorData::~QCursorData () from /usr/lib/libqt-mt.so.3
#7  0xb70799c5 in QCursor::~QCursor () from /usr/lib/libqt-mt.so.3
#8  0xb707a459 in QCursor::handle () from /usr/lib/libqt-mt.so.3
#9  0xb69a4854 in __cxa_finalize () from /lib/tls/i686/cmov/libc.so.6
#10 0xb705aca3 in ?? () from /usr/lib/libqt-mt.so.3
#11 0xb75c9fe0 in ?? () from /usr/lib/libqt-mt.so.3
#12 0xb76a47e8 in ?? ()
#13 0xbfc983b8 in ?? ()
#14 0xb705ac7a in ?? () from /usr/lib/libqt-mt.so.3
#15 0xbfc983e0 in ?? ()
#16 0xb75bc460 in ?? () from /usr/lib/libqt-mt.so.3
#17 0xbfc983c8 in ?? ()
#18 0xb74e860b in _fini () from /usr/lib/libqt-mt.so.3
#19 0xb74e860b in _fini () from /usr/lib/libqt-mt.so.3
#20 0xb7f938f4 in _dl_rtld_di_serinfo () from /lib/ld-linux.so.2
#21 0xb69a45e7 in exit () from /lib/tls/i686/cmov/libc.so.6
#22 0xb705aff8 in qt_badwindow () from /usr/lib/libqt-mt.so.3
#23 0xb7765f59 in KApplication::xioErrhandler () from /usr/lib/libkdecore.so.4
#24 0xb7765f97 in KApplication::xioErrhandler () from /usr/lib/libkdecore.so.4
#25 0xb6c49e9d in _XIOError (dpy=0x813ac58) at ../../src/XlibInt.c:2913
#26 0xb6c4b2f6 in _XFlushInt (dpy=0x813ac58, cv=0x0)
    at ../../src/XlibInt.c:690
#27 0xb6c270ba in XDrawLine (dpy=0x813ac58, d=56623829, gc=0x8457ac8, x1=-4,
    y1=-4, x2=-4, y2=-4) at ../../src/DrLine.c:76
#28 0xb7097c2e in QPainter::drawLine () from /usr/lib/libqt-mt.so.3
#29 0xb67b097f in LipstikStyle::renderSurface ()
   from /usr/lib/kde3/plugins/styles/lipstik.so
#30 0xb67b529b in LipstikStyle::drawKStylePrimitive ()
   from /usr/lib/kde3/plugins/styles/lipstik.so
#31 0xb760415b in KStyle::drawComplexControl () from /usr/lib/libkdefx.so.4
#32 0xb67b67d2 in LipstikStyle::drawComplexControl ()
   from /usr/lib/kde3/plugins/styles/lipstik.so
#33 0xb728015d in QSlider::paintEvent () from /usr/lib/libqt-mt.so.3
#34 0xb718176f in QWidget::event () from /usr/lib/libqt-mt.so.3
#35 0xb70ddf80 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#36 0xb70decf6 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#37 0xb7819e37 in KApplication::notify () from /usr/lib/libkdecore.so.4
#38 0xb706edb7 in QApplication::sendEvent () from /usr/lib/libqt-mt.so.3
#39 0xb70aa2d5 in QWidget::repaint () from /usr/lib/libqt-mt.so.3
#40 0xb70df48b in QApplication::sendPostedEvents ()
   from /usr/lib/libqt-mt.so.3
#41 0xb70df5aa in QApplication::sendPostedEvents ()
   from /usr/lib/libqt-mt.so.3
#42 0xb7081f4f in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#43 0xb70f5cfb in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#44 0xb70f5c1e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#45 0xb70dcc13 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#46 0x0806c92f in ?? ()
#47 0xb698dea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#48 0x080696e1 in ?? ()

---

### Post by GeneralZod on 2006-01-04
Make sure all of your KDE stuff is 100% up-to-date - there have been quite a few bug-fixes since the initial release, and this sounds like a manifestation of one of these old bugs :)

---

### Post by mpierce on 2006-01-04
Yes - I did that as I run sudo apt-get update virtually everyday and then use synaptic. I think I may try to uninstall and then do a reinstall if it will allow this.

---

### Post by mpierce on 2006-01-04
My thread can end as a solution was found in another thread posted almost simultaneously when I posted mine. Many thanks to byourg for posting what has turned out to be the solution:

"install kaffeine-xine, then start kaffeine and go to settings, player engine and select kaffeine, not the kaffeine gstreamer, for the engine. I had to do this to get DVD playback. Hope this helps?"

End thread...

---

### Post by f1dave on 2006-01-04
Keep in mind that an update/upgrade wont do anything unless you have the newest repositories in there. For KDE 3.5.1 for instance, which comes out Jan 20th from memory, you'll need to add an extra repository to grab all the new goodies.

---

