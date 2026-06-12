---
title: "Gnome-Commander Problem : segfault error in libc-2.8.90.so"
date: 2009-03-14
forum: General Help
---

### Post by jmlaniel on 2009-03-14
For no apparent reason(to me, at least), I am now unable to start gnome-commander. I am running Ubuntu 8.10 with gnome. When I try to start gnome-commander, the system appears to start the application but then, nothing happens. Worst of all, the application was working perfectly fine a few days ago!!!

I tried searching the logs and found this in kern.log, messages and syslog:

Mar 14 11:27:08 Philemon kernel: [  959.351660] gnome-commander[7348]: segfault at 0 ip b6f40d88 sp bff8c5fc error 4 in libc-2.8.90.so[b6eca000+158000]

I really don't know what this log is supposed to means...

I tried reinstalling gnome-commander, my kernel, the libc6 library (which contains the libc-2.8.90.so file) without any positive results.

The only thing that can be related to this problem is that I had a hard disk crash a few days ago. I repaired manually the system with fsck and I think that I lost some files... If this is related to my problem, is there any way I can salvage the system without a reinstallation?

So, does anyone knows what happen and what I can do?

---

### Post by jmlaniel on 2009-03-15
** bump **

---

### Post by jmlaniel on 2009-03-16
No suggestions? Is there any solution beside reinstalling???

---

