---
title: "kRunner keeps starting and crashing"
date: 2011-05-02
forum: Desktop Environments
---

### Post by Raevyn on 2011-05-02
Hello

I was hoping someone can help me. I am running ubuntu 10.10, and I wanted to try KDE. So i downloaded and installed it, but when I go to run KDE, the desktop comes up and then I get an error report screen for krunner. If I close it, another pops... if I dont close it then a new window pops up saying something happened to krunner. What the message is I was finally able to get  (see below). I did try logging into KDE into a new user account (one that was totally new.. no profile info was created before) and the same thing was happening on that account as well. Does anyone know how to fix this?

[COLOR=#000000][FONT=Sans][SIZE=3]Application: Run Command Interface (krunner), signal: Segmentation fault[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3][Current thread is 1 (Thread 0x7f1a76b51780 (LWP 3396))][/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Sans][SIZE=3]Thread 2 (Thread 0x7f1a5edb2700 (LWP 3397)):[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#0  0x00007f1a76584203 in __poll (fds=<value optimized out>, nfds=<value optimized out>, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:87[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#1  0x00007f1a6bfb2009 in ?? () from /lib/libglib-2.0.so.0[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#2  0x00007f1a6bfb245c in g_main_context_iteration () from /lib/libglib-2.0.so.0[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#3  0x00007f1a72f861e6 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#4  0x00007f1a72f58a02 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#5  0x00007f1a72f58dec in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#6  0x00007f1a72e632fd in QThread::exec() () from /usr/lib/libQtCore.so.4[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#7  0x00007f1a72f385f8 in ?? () from /usr/lib/libQtCore.so.4[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#8  0x00007f1a72e6627e in ?? () from /usr/lib/libQtCore.so.4[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#9  0x00007f1a6c470971 in start_thread (arg=<value optimized out>) at pthread_create.c:304[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#10 0x00007f1a7659092d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#11 0x0000000000000000 in ?? ()[/SIZE][/FONT][/COLOR]
 

 [COLOR=#000000][FONT=Sans][SIZE=3]Thread 1 (Thread 0x7f1a76b51780 (LWP 3396)):[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3][KCrash Handler][/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#6  0x00007f1a6f016880 in KUriFilterSearchProvider::setName(QString const&) () from /usr/lib/libkio.so.5[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#7  0x00007f1a6f018c42 in KUriFilterPlugin::setPreferredSearchProviders(KUriFilterData&, QHash<QString, QPair<QString, QString> > const&) const () from /usr/lib/libkio.so.5[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#8  0x00007f1a58221c1c in ?? () from /usr/lib/kde4/kuriikwsfilter.so[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#9  0x00007f1a6f016f0c in KUriFilter::filterUri(KUriFilterData&, QStringList const&) () from /usr/lib/libkio.so.5[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#10 0x00007f1a6f01a58c in KUriFilter::filterSearchUri(KUriFilterData&, QFlags<KUriFilter::SearchFilterType>) () from /usr/lib/libkio.so.5[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#11 0x00007f1a58a5aa9d in ?? () from /usr/lib/kde4/krunner_webshortcuts.so[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#12 0x00007f1a58a5b21a in ?? () from /usr/lib/kde4/krunner_webshortcuts.so[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#13 0x00007f1a58a5c3c7 in QObject* KPluginFactory::createInstance<WebshortcutRunner, QObject>(QWidget*, QObject*, QList<QVariant> const&) () from /usr/lib/kde4/krunner_webshortcuts.so[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#14 0x00007f1a734d3aa1 in KPluginFactory::create(char const*, QWidget*, QObject*, QList<QVariant> const&, QString const&) () from /usr/lib/libkdecore.so.5[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#15 0x00007f1a75a83040 in ?? () from /usr/lib/libplasma.so.3[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#16 0x00007f1a75a841e8 in ?? () from /usr/lib/libplasma.so.3[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#17 0x00007f1a75a81b41 in Plasma::RunnerManager::reloadConfiguration() () from /usr/lib/libplasma.so.3[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#18 0x00007f1a76857d31 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_krunner.so[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#19 0x00007f1a76858493 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_krunner.so[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#20 0x00007f1a768584e5 in ?? () from /usr/lib/kde4/libkdeinit/libkdeinit4_krunner.so[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#21 0x00007f1a76858f2d in kdemain () from /usr/lib/kde4/libkdeinit/libkdeinit4_krunner.so[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#22 0x00007f1a764c8d8e in __libc_start_main (main=<value optimized out>, argc=<value optimized out>, ubp_av=<value optimized out>, init=<value optimized out>, fini=<value optimized out>, rtld_fini=<value optimized out>, stack_end=0x7fff4d0e8b58) at libc-start.c:226[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Sans][SIZE=3]#23 0x0000000000400669 in _start ()[/SIZE][/FONT][/COLOR]

---

### Post by Raevyn on 2011-05-03
Okay I got it working! I just had to update all of my packages.

---

