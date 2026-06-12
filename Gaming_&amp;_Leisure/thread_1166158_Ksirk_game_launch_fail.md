---
title: "Ksirk game launch fail"
date: 2009-05-21
forum: Gaming &amp; Leisure
---

### Post by mitoman on 2009-05-21
So I'm still pretty new to ubuntu/linux life, but slowly figuring things out.  I tried to install Ksirk (a Risk strategy clone).  It seems to install fine and the game will open.  But when I go to a new game and try to actually launch and play I get this error


 p, li { white-space: pre-wrap; }  The application KsirK (ksirk) crashed and caused the signal 11 (SIGSEGV).
Please help us improve the software you use by filing a report at [[COLOR=#0057ae]_http://bugs.kde.org_[/COLOR]]("http://bugs.kde.org/"). Useful details include how to reproduce the error, documents that were loaded, etc.

Then in details it says this (sorry its long)

 p, li { white-space: pre-wrap; }  This backtrace appears to be of no use.
 This is probably because your packages are built in a way which prevents creation of proper backtraces, or the stack frame was seriously corrupted in the crash.
 
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
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
 [New Thread 0x7f94ba16d750 (LWP 7283)]
 [New Thread 0x7f949b7fd950 (LWP 7296)]
 [New Thread 0x7f949bffe950 (LWP 7295)]
 [New Thread 0x7f94a4dee950 (LWP 7294)]
 [New Thread 0x7f94a5a00950 (LWP 7285)]
 [New Thread 0x7f94a6a70950 (LWP 7284)]
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 0x00007f94b5c5192f in waitpid () from /lib/libc.so.6
 [Current thread is 0 (LWP 7283)]
 
 Thread 6 (Thread 0x7f94a6a70950 (LWP 7284)):
 #0  0x00007f94b599956d in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
 #1  0x00007f94a87bbf91 in ?? () from /usr/lib/libxine.so.1
 #2  0x00007f94b59953ba in start_thread () from /lib/libpthread.so.0
 #3  0x00007f94b5c8ffcd in clone () from /lib/libc.so.6
 #4  0x0000000000000000 in ?? ()
 
 Thread 5 (Thread 0x7f94a5a00950 (LWP 7285)):
 #0  0xffffffffff6001bb in ?? ()
 #1  0x00007f94a59ffd50 in ?? ()
 #2  0x00007fffc21fe5fc in ?? ()
 Backtrace stopped: previous frame identical to this frame (corrupt stack?)
 
 Thread 4 (Thread 0x7f94a4dee950 (LWP 7294)):
 #0  0x00007f94b5c86496 in poll () from /lib/libc.so.6
 #1  0x00007f94a5e2de3d in ?? () from /usr/lib/libpulse.so.0
 #2  0x00007f94a5e205a9 in pa_mainloop_poll () from /usr/lib/libpulse.so.0
 #3  0x00007f94a5e21bf8 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
 #4  0x00007f94a5e21cc0 in pa_mainloop_run () from /usr/lib/libpulse.so.0
 #5  0x00007f94a5e2dc3d in ?? () from /usr/lib/libpulse.so.0
 #6  0x00007f94a5e51e10 in ?? () from /usr/lib/libpulse.so.0
 #7  0x00007f94b59953ba in start_thread () from /lib/libpthread.so.0
 #8  0x00007f94b5c8ffcd in clone () from /lib/libc.so.6
 #9  0x0000000000000000 in ?? ()
 
 Thread 3 (Thread 0x7f949bffe950 (LWP 7295)):
 #0  0x00007f94b5c86496 in poll () from /lib/libc.so.6
 #1  0x00007f94a4ffa969 in ?? () from /usr/lib/xine/plugins/1.26/xineplug_ao_out_alsa.so
 #2  0x00007f94b59953ba in start_thread () from /lib/libpthread.so.0
 #3  0x00007f94b5c8ffcd in clone () from /lib/libc.so.6
 #4  0x0000000000000000 in ?? ()
 
 Thread 2 (Thread 0x7f949b7fd950 (LWP 7296)):
 #0  0x00007f94b59992e9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
 #1  0x00007f94a87cd353 in ?? () from /usr/lib/libxine.so.1
 #2  0x00007f94b59953ba in start_thread () from /lib/libpthread.so.0
 #3  0x00007f94b5c8ffcd in clone () from /lib/libc.so.6
 #4  0x0000000000000000 in ?? ()
 
 Thread 1 (Thread 0x7f94ba16d750 (LWP 7283)):
 #0  0x00007f94b5c5192f in waitpid () from /lib/libc.so.6
 #1  0x00007f94b8099423 in ?? () from /usr/lib/libkdeui.so.5
 #2  0x00007f94b809a2cb in KCrash::defaultCrashHandler () from /usr/lib/libkdeui.so.5
 #3  <signal handler called>
 #4  0x00000000004719ab in ?? ()
 #5  0x000000000044a1b1 in ?? ()
 #6  0x00007f94b746f1f2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
 #7  0x00000000004ed70d in ?? ()
 #8  0x00007f94b68ed768 in QWidget::event () from /usr/lib/libQtGui.so.4
 #9  0x00007f94b6c8740b in QFrame::event () from /usr/lib/libQtGui.so.4
 #10 0x00007f94b6ea3d1b in QGraphicsView::viewportEvent () from /usr/lib/libQtGui.so.4
 #11 0x00000000004ed81e in ?? ()
 #12 0x00007f94b7458a68 in QCoreApplicationPrivate::sendThroughObjectEventFilters () from /usr/lib/libQtCore.so.4
 #13 0x00007f94b689c75c in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
 #14 0x00007f94b68a50da in QApplication::notify () from /usr/lib/libQtGui.so.4
 #15 0x00007f94b803426b in KApplication::notify () from /usr/lib/libkdeui.so.5
 #16 0x00007f94b745975c in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
 #17 0x00007f94b68a4328 in QApplicationPrivate::sendMouseEvent () from /usr/lib/libQtGui.so.4
 #18 0x00007f94b68a48a2 in QApplicationPrivate::sendSyntheticEnterLeave () from /usr/lib/libQtGui.so.4
 #19 0x00007f94b68f2d1a in QWidget::setVisible () from /usr/lib/libQtGui.so.4
 #20 0x00007f94b68d6905 in QStackedLayout::setCurrentIndex () from /usr/lib/libQtGui.so.4
 #21 0x000000000046b088 in ?? ()
 #22 0x0000000000434e33 in _start ()
 #0  0x00007f94b5c5192f in waitpid () from /lib/libc.so.6
 



I suspect its not a bug and that I've just not installed something right.  I love Risk and would like to play this so any help would be greatly appreciated.

I've installed the latest Ubuntu (9.04).  Also installed the KDE stuff (Kubuntu-Desktop, libkdegames, and the libkdegames-dev package).  I can't get it to work under either dekstop.

I may be totally off base on what I'm doing here, but I'm eager to learn.  Thanks for any help!!

---

### Post by Squash101 on 2009-12-03
You are not alone in having this problem. I have also experienced it, and, when searching through the forums, I have found several other people with the same problem. What's most surprising is that most of these posts have received no response!

My experiences with the helpful people at these forums have been different- many of the reported problems get discussed and resolved very effectively.

Were you able to ultimately resolve? Did you abandon the idea? Find an alternative to Ksirk? I'm interested.

---

### Post by lucio39 on 2009-12-05
> **Squash101 said:**
> You are not alone in having this problem. I have also experienced it, and, when searching through the forums, I have found several other people with the same problem.

Were you able to ultimately resolve? Did you abandon the idea? Find an alternative to Ksirk? I'm interested.

I'm having the same problem; I'll keep you posted on any progress.
Good luck!

---

### Post by Squash101 on 2009-12-14
I re-installed the graphics drivers and the problem was solved.

---

