---
title: "Dolphin not starting/crashing"
date: 2012-05-12
forum: Desktop Environments
---

### Post by ronaldbrijo on 2012-05-12
I am trying to open Dolphin Manager but it keeps crashing.. 

I am using 12.04.

Here is the crash report info.

"  p, li { white-space: pre-wrap; }  Application: Dolphin (dolphin), signal: Segmentation fault
 Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
 [Current thread is 1 (Thread 0x7f1aaef20780 (LWP 5495))]
 

 Thread 2 (Thread 0x7f1a9a89a700 (LWP 5496)):
 #0  0x00007f1aae7e60bd in read () from /lib/x86_64-linux-gnu/libc.so.6
 #1  0x00007f1aa680588f in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #2  0x00007f1aa67caabd in g_main_context_check () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #3  0x00007f1aa67caf96 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #4  0x00007f1aa67cb124 in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
 #5  0x00007f1aab879426 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #6  0x00007f1aab848c82 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #7  0x00007f1aab848ed7 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #8  0x00007f1aab747fa7 in QThread::exec() () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #9  0x00007f1aab8289ff in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #10 0x00007f1aab74afcb in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
 #11 0x00007f1aa708fe9a in start_thread () from /lib/x86_64-linux-gnu/libpthread.so.0
 #12 0x00007f1aae7f34bd in clone () from /lib/x86_64-linux-gnu/libc.so.6
 #13 0x0000000000000000 in ?? ()
 

 Thread 1 (Thread 0x7f1aaef20780 (LWP 5495)):
 [KCrash Handler]
 #6  0x00007f1aadb67e0b in ?? () from /usr/lib/libdolphinprivate.so.4
 #7  0x00007f1aadb6919a in ?? () from /usr/lib/libdolphinprivate.so.4
 #8  0x00007f1aadb4f280 in DolphinItemListContainer::DolphinItemListContainer(KDirLister*, QWidget*) () from /usr/lib/libdolphinprivate.so.4
 #9  0x00007f1aadb558cf in DolphinView::DolphinView(KUrl const&, QWidget*) () from /usr/lib/libdolphinprivate.so.4
 #10 0x00007f1aaeb0098c in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_dolphin.so
 #11 0x00007f1aaeaf141c in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_dolphin.so
 #12 0x00007f1aaeafb38b in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_dolphin.so
 #13 0x00007f1aaeaef287 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_dolphin.so
 #14 0x00007f1aaeb064aa in kdemain () from /usr/lib/kde4/libkdeinit/libkdeinit4_dolphin.so
 #15 0x00007f1aae72276d in __libc_start_main () from /lib/x86_64-linux-gnu/libc.so.6
 #16 0x0000000000400671 in _start ()"


Is there another file manager i can install?


thank you:confused:

---

