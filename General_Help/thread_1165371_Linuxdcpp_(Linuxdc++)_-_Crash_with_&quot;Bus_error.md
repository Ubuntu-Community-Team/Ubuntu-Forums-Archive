---
title: "Linuxdcpp (Linuxdc++) - Crash with &quot;Bus error&quot; when hashing"
date: 2009-05-20
forum: General Help
---

### Post by wewek on 2009-05-20
Hello,
I got this error (Bus error) when I enabled compiz (Ubuntu 8.10).
I haven't used compiz before and linuxdc++ ran well.
But now linuxdc++ crashes every time after few minutes. Disabling compiz or deleting ~/.dc++ didn't help.
Any idea how to fix it? Or what's the workaround?
Thank you.

$ linuxdcpp 
Loading: Hash database
Loading: Shared Files
Loading: Download Queue
Bus error
$

See also: [https://bugs.edge.launchpad.net/linuxdcpp/+bug/311478](https://bugs.edge.launchpad.net/linuxdcpp/+bug/311478)

---

### Post by piyush.neo on 2011-03-10
Do you got any solution for it. One of my friends is also facing the same problem. Here is u/p from GDB

```
(gdb) run
Starting program: /usr/bin/linuxdcpp 
[Thread debugging using libthread_db enabled]
Loading: Hash database
[New Thread 0xb7d7ab70 (LWP 2106)]
Loading: Shared Files
[New Thread 0xb7579b70 (LWP 2107)]

Program received signal SIGBUS, Bus error.
[Switching to Thread 0xb7d7ab70 (LWP 2106)]
0x00b1f290 in ?? () from /lib/libc.so.6
(gdb) backtrace
#0  0x00b1f290 in ?? () from /lib/libc.so.6
#1  0x0810e02f in ?? ()
#2  0x08093077 in ?? ()
#3  0x080aa01b in ?? ()
#4  0x080abf1b in ?? ()
#5  0x08109b6f in ?? ()
#6  0x006e6cc9 in start_thread () from /lib/libpthread.so.0
#7  0x00adb69e in clone () from /lib/libc.so.6
```

Can anybody help it out?

---

