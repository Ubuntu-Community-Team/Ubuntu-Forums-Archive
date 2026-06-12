---
title: "Gnome Panels Segmentation Fault"
date: 2010-06-09
forum: Desktop Environments
---

### Post by jin15 on 2010-06-09
Hi guys, i've a strange problem. All the applets of gnome-panels are disappeared and when i try to add other appets gnome-panels restart. Also other applications like Rhythmbox or Deluge or Brasero when i try to lunch them there's a segmentation fault. With GDB i discovered that this is the problem:
 ```
Program received signal SIGSEGV, Segmentation fault.
0x00d9c241 in strncmp () from /lib/tls/i686/cmov/libc.so.6
```But I don't know how i can solve it.....please help me.


P.S. = Yesterday i upgraded my ubuntu from 9.10 to 10.04 but i've always the same problem.

---

### Post by jin15 on 2010-06-11
Please help me :(

---

