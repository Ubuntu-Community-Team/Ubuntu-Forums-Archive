---
title: "Evolution 2.28.3 crashes on ubuntu 10.04 Lucid Lynx"
date: 2010-06-17
forum: Desktop Environments
---

### Post by kahnoie on 2010-06-17
Evolution keeps crashing
evolution[1167]: segfault at 2c ip 06c4e959 sp b39aaf30 error 4 in libglib-2.0.so.0.2400.1[6bf5000+c8000]

uname -a
Linux amit-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

Evolution 2.28.3
Ubuntu 10.04 LTS - the Lucid Lynx

---

### Post by kahnoie on 2010-06-18
13131.958054] evolution[8199]: segfault at 5 ip 011f7959 sp bfc39da0 error 4 in libglib-2.0.so.0.2400.1[119e000+c8000]
[17001.820803] evolution[16459]: segfault at 69616d24 ip 00ccc39a sp bfb09a80 error 4 in libdbus-1.so.3.4.0[cc2000+37000]
[19376.815894] evolution[18266]: segfault at 4 ip 0012339a sp bfb956c0 error 4 in libdbus-1.so.3.4.0[119000+37000]
[24988.991571] evolution[20741]: segfault at a ip 07581959 sp bfe2a5e0 error 4 in libglib-2.0.so.0.2400.1[7528000+c8000]

---

### Post by grossvogel on 2010-07-23
I'm seeing similar crashes on x64:

[  157.526344] evolution[2007] general protection ip:7f52f5d50108 sp:7fffaf379580 error:420 in libeutil.so.0.0.0[7f52f5d27000+46000]

[  202.195169] evolution[2109]: segfault at 2d ip 000000000000002d sp 00007fff20e09668 error 14 in evolution[400000+20000]

uname -a
Linux boxen 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

Evolution 2.28.3
Ubuntu 10.04 LTS - the Lucid Lynx

---

### Post by Nrip Cheema on 2011-01-11
The evolution work normally but it crashes in the middle. Most of the time it shows synchronizing the mailbox folders; The following is the error message: 

evolution[8067]: segfault at 30 ip 00000030 sp bfbdf88c error 14 in evolution[8048000+1d000]


Sys configuration: 10.04, 2.6.32-27-generic

---

