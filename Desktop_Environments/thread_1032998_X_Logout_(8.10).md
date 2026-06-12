---
title: "X Logout (8.10)"
date: 2009-01-06
forum: Desktop Environments
---

### Post by pete_keller on 2009-01-06
Randomly X will log me out.  It happens more often if I am playing gPlanetary.

Below is the backtrace 

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xffffe420]
2: [0xffffe420]
3: /usr/X11R6/bin/X(WriteEventsToClient+0x1ca) [0x80959ca]
4: /usr/X11R6/bin/X(TryClientEvents+0xe8) [0x8095ac8]
5: /usr/X11R6/bin/X(DeliverEventsToWindow+0x296) [0x8096436]
6: /usr/X11R6/bin/X(DeliverDeviceEvents+0x18b) [0x8096b8b]
7: /usr/X11R6/bin/X(CoreProcessPointerEvent+0x2c6) [0x809a096]
8: /usr/X11R6/bin/X(ProcessPointerEvent+0xae) [0x819c55e]
9: /usr/X11R6/bin/X(mieqProcessInputEvents+0x172) [0x8110282]
10: /usr/X11R6/bin/X(ProcessInputEvents+0x2c) [0x80c39bc]
11: /usr/X11R6/bin/X(Dispatch+0x6e) [0x808c5be]
12: /usr/X11R6/bin/X(main+0x47d) [0x8071d1d]
13: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7bf1685]
14: /usr/X11R6/bin/X [0x8071101]
Saw signal 11.  Server aborting.

Thanks
Pete

---

