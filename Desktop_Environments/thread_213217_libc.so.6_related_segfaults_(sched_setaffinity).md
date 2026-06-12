---
title: "libc.so.6 related segfaults (sched_setaffinity)"
date: 2006-07-11
forum: Desktop Environments
---

### Post by tbennett on 2006-07-11
Just cd install of Drake 6.06 and everything was working.  I then did a system upgrade to the latest and gratest (apt-get dist-upgrade) and I now a number of programs segfault.

It happens with;

*xemacs
*firefox
*office and many others

I ran gbd over xemacs and office and they both seg faulted at the same point

----
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1214929216 (LWP 6535)]
0xb7b798d1 in sched_setaffinity () from /lib/tls/i686/cmov/libc.so.6
(gdb)
(gdb) exit
----

I did a google search for "sched_setaffinity () from /lib/tls/i686/cmov/libc.so.6" and nothing comes up.  

Anyone got any ideas?

---

