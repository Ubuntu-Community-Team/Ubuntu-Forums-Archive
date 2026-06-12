---
title: "K mail Crash"
date: 2009-08-24
forum: Desktop Environments
---

### Post by Rajwinder on 2009-08-24
i am using K mail.Most of the times i empty the trash following error occurs.
A Fatal Error Occurred
The application KMail (kmail) crashed and caused the signal 6 (SIGABRT).Any help

---

### Post by macogw on 2009-08-24
Are you using IMAP?  It's rather unstable.  Maybe try using Disconnected IMAP instead.

---

### Post by Rajwinder on 2009-08-25
No I am using POP and error is as follows
Application: Kontact (kontact), signal SIGABRT
[Current thread is 0 (LWP 7482)]

Thread 2 (Thread 0xaf167b90 (LWP 7489)):
#0  0xb7fb4430 in __kernel_vsyscall ()
#1  0xb59127b1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb5be6380 in ?? () from /usr/lib/libQtCore.so.4
#3  0xb5b1496e in ?? () from /usr/lib/libQtCore.so.4
#4  0xb510b4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0xb591a49e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb4825700 (LWP 7482)):
[KCrash Handler]
#6  0xb7fb4430 in __kernel_vsyscall ()
#7  0xb58616d0 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb5863098 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb5b0c595 in qt_message_output () from /usr/lib/libQtCore.so.4
#10 0xb5b0c681 in qFatal () from /usr/lib/libQtCore.so.4
#11 0xb5b0c775 in qt_assert () from /usr/lib/libQtCore.so.4
#12 0xb0b85749 in ?? () from /usr/lib/libkmailprivate.so.4
#13 0xb06c7ce3 in ?? () from /usr/lib/libkmailprivate.so.4
#14 0xb5c1eca8 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#15 0xb5c1f932 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#16 0xb5c5a717 in QTimer::timeout () from /usr/lib/libQtCore.so.4
#17 0xb5c246fe in QTimer::timerEvent () from /usr/lib/libQtCore.so.4
#18 0xb5c1915f in QObject::event () from /usr/lib/libQtCore.so.4
#19 0xb60d9e9c in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#20 0xb60e219e in QApplication::notify () from /usr/lib/libQtGui.so.4
#21 0xb6cfd94d in KApplication::notify () from /usr/lib/libkdeui.so.5
#22 0xb5c08a3b in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#23 0xb5c37d71 in ?? () from /usr/lib/libQtCore.so.4
#24 0xb5c344e0 in ?? () from /usr/lib/libQtCore.so.4
#25 0xb4cdbb88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#26 0xb4cdf0eb in ?? () from /usr/lib/libglib-2.0.so.0
#27 0xb4cdf268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#28 0xb5c34438 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#29 0xb617b365 in ?? () from /usr/lib/libQtGui.so.4
#30 0xb5c0706a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#31 0xb5c074aa in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#32 0xb5c09959 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#33 0xb60d9d17 in QApplication::exec () from /usr/lib/libQtGui.so.4
#34 0x0804c072 in _start ()

---

