---
title: "kde aplication (krusader) crash"
date: 2010-02-21
forum: Desktop Environments
---

### Post by fraktik on 2010-02-21
I have some problems with kde aplication on my 8.10 (interpid) for a while.
For example my **krusader** crashed everytime, when i am traying to start him.

Critical error:
> Aplikace: Krusader (krusader), signál SIGSEGV
[Current thread is 0 (LWP 10468)]

Thread 2 (Thread 0xacb99b90 (LWP 10469)):
#0  0xb8023430 in __kernel_vsyscall ()
#1  0xb6591df1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb731f150 in ?? () from /usr/lib/libQtCore.so.4
#3  0xb724f6ae in ?? () from /usr/lib/libQtCore.so.4
#4  0xb614150f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0xb6599a0e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb5cc18d0 (LWP 10468)):
[KCrash Handler]
#6  0x08087e58 in _start ()

Removing files from */home/fraktik/.kde/share/apps/krusader* dont change anything.

**K3b** on start:
*Isnt possible to comunicate with aplication klauncher* (its my translation from czech :-( )
 But K3b finally start, so its not so tragic. Some app. (like konqueror, kate, dolphin or  for ex.) are totaly OK, others (like krusader, kaffeine or amarok sometime) dont even start.

Any ideas please?

---

