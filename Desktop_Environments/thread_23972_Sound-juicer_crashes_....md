---
title: "Sound-juicer crashes ..."
date: 2005-04-04
forum: Desktop Environments
---

### Post by ploum on 2005-04-04
When I hit the "extract" button in Sound-Juicer, it segfaults...

I'm using a freshly installed Hoary, so it cannot be a bad profile or something.  Sound-juicer was upgraded today, so I was hoping...but not :-(

The only thing I can do is give the gdb output of the crash (not sure it's useful) :


[Thread -1238377552 (LWP 26286) exited]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1224994688 (LWP 26281)]
0xb742f77a in mallopt () from /lib/tls/i686/cmov/libc.so.6

---

