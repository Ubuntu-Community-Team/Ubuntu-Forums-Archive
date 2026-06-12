---
title: "Plasma Workspace Crash"
date: 2008-12-18
forum: General Help
---

### Post by Wake Rider on 2008-12-18
I keep getting this error saying Plasma Workspace has crashed on Kubuntu 8.10. However the screen only blanks out white for a second and then everything comes back completely as normal. Even though my system is fine afterwards, can someone please explain what the Plasma Workspace is and why it keeps crashing. Here is the error report:

> Application: Plasma Workspace (plasma), signal SIGABRT
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
[New Thread 0x7f70f1ac4730 (LWP 5633)]
[New Thread 0x4147d950 (LWP 5786)]
[New Thread 0x41f1f950 (LWP 5785)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#5  0x00007f70f152ffd5 in raise () from /lib/libc.so.6
#6  0x00007f70f1531b43 in abort () from /lib/libc.so.6
#7  0x00007f70f03106b5 in qt_message_output () from /usr/lib/libQtCore.so.4
#8  0x00007f70f03107fd in qFatal () from /usr/lib/libQtCore.so.4
#9  0x00007f70df704d2a in ?? () from /usr/lib/kde4/plasma_applet_pager.so
#10 0x00007f70f11de3b9 in Plasma::Applet::paint ()
   from /usr/lib/libplasma.so.2
#11 0x00007f70ef6d4165 in ?? () from /usr/lib/libQtGui.so.4
#12 0x00007f70ef6d7988 in ?? () from /usr/lib/libQtGui.so.4
#13 0x00007f70ef6d7dea in QGraphicsScene::drawItems ()
   from /usr/lib/libQtGui.so.4
#14 0x00007f70ef6f5fdb in QGraphicsView::paintEvent ()
   from /usr/lib/libQtGui.so.4
#15 0x00007f70ef1f3114 in QWidget::event () from /usr/lib/libQtGui.so.4
#16 0x00007f70ef6f09bb in QGraphicsView::viewportEvent ()
   from /usr/lib/libQtGui.so.4
#17 0x00007f70f0400038 in QCoreApplicationPrivate::sendThroughObjectEventFilters () from /usr/lib/libQtCore.so.4
#18 0x00007f70ef1a0c0c in QApplicationPrivate::notify_helper ()
   from /usr/lib/libQtGui.so.4
#19 0x00007f70ef1a89ba in QApplication::notify () from /usr/lib/libQtGui.so.4
#20 0x00007f70f0d5cfcb in KApplication::notify () from /usr/lib/libkdeui.so.5
#21 0x00007f70f0400d61 in QCoreApplication::notifyInternal ()
   from /usr/lib/libQtCore.so.4
#22 0x00007f70ef1f1b4f in QWidgetPrivate::drawWidget ()
   from /usr/lib/libQtGui.so.4
#23 0x00007f70ef1f2232 in QWidgetPrivate::paintSiblingsRecursive ()
   from /usr/lib/libQtGui.so.4
#24 0x00007f70ef1f215b in QWidgetPrivate::paintSiblingsRecursive ()
   from /usr/lib/libQtGui.so.4
#25 0x00007f70ef1f1808 in QWidgetPrivate::drawWidget ()
   from /usr/lib/libQtGui.so.4
#26 0x00007f70ef34b664 in ?? () from /usr/lib/libQtGui.so.4
#27 0x00007f70ef34bb17 in ?? () from /usr/lib/libQtGui.so.4
#28 0x00007f70ef1f2f35 in QWidget::event () from /usr/lib/libQtGui.so.4
#29 0x00007f70ef57ac99 in QAbstractScrollArea::event ()
   from /usr/lib/libQtGui.so.4
#30 0x00007f70ef1a0c3d in QApplicationPrivate::notify_helper ()
   from /usr/lib/libQtGui.so.4
#31 0x00007f70ef1a89ba in QApplication::notify () from /usr/lib/libQtGui.so.4
#32 0x00007f70f0d5cfcb in KApplication::notify () from /usr/lib/libkdeui.so.5
#33 0x00007f70f0400d61 in QCoreApplication::notifyInternal ()
   from /usr/lib/libQtCore.so.4
#34 0x00007f70f04019fa in QCoreApplicationPrivate::sendPostedEvents ()
   from /usr/lib/libQtCore.so.4
#35 0x00007f70f04294d3 in ?? () from /usr/lib/libQtCore.so.4
#36 0x00007f70eae70d3b in g_main_context_dispatch ()
   from /usr/lib/libglib-2.0.so.0
#37 0x00007f70eae7450d in ?? () from /usr/lib/libglib-2.0.so.0
#38 0x00007f70eae746cb in g_main_context_iteration ()
   from /usr/lib/libglib-2.0.so.0
#39 0x00007f70f042915f in QEventDispatcherGlib::processEvents ()
   from /usr/lib/libQtCore.so.4
#40 0x00007f70ef232a6f in ?? () from /usr/lib/libQtGui.so.4
#41 0x00007f70f03ff682 in QEventLoop::processEvents ()
   from /usr/lib/libQtCore.so.4
#42 0x00007f70f03ff80d in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#43 0x00007f70f0401cbd in QCoreApplication::exec ()
   from /usr/lib/libQtCore.so.4
#44 0x00007f70f188afe3 in kdemain () from /usr/lib/libkdeinit4_plasma.so
#45 0x00007f70f151b466 in __libc_start_main () from /lib/libc.so.6
#46 0x0000000000400659 in _start ()
#0  0x00007f70f15a5621 in nanosleep () from /lib/libc.so.6


---

### Post by funnymansteve on 2009-01-23
I have recieved the same error twice but everthing was fine a few seconds later. Now the screen just stays blank and its been like that for 20 minutes. I've restarted twice with same result.

Any thoughts ?

---

### Post by walmartshopper67 on 2009-03-12
Hate to be a latecomer, but i'm having the same problem for the most part. It's infuriating - plasma seems to be about as stable as Windows ME. I've run into quite a few posts on many different Linux related forums, most of which didnt work at all. I've installed Kubuntu Intrepid 3 times in 3 days because of this. The only solution that worked even a little bit was to delete (or move) my ~/.kde folder. That cleared it up once, but ive tried it again and it failed. 

Right now i'm on my 3rd install, and enabling all the debugging things, so maybe i'll be able to narrow it down. It kinda sucks though.:(

---

