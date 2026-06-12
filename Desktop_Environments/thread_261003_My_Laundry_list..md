---
title: "My Laundry list."
date: 2006-09-19
forum: Desktop Environments
---

### Post by GQed76 on 2006-09-19
I have a few issues I hope people can help me sort out.

1.) On boot I get a message stating my boot sector doesnt match the backup, so it won't fix it.  I get this when I boot and it goes to filesystem.  It doesn't impact they system at all, just an annoyance.

2.) When I try and complie a new kernel from Kernel.org, I always loose the usplash.  Im a big eyecandy person, so having a black screen until I get into the gdm logon is a big turn off for me.

3.) I was thrilled when I got a new D-Link WDA-1320 card and Dapper installed it automagically.
I cried when I installed the aforementioned kernel from kernel.org and it was no longer detected.  I am very new to Kernel compling, so any walk throughs on how to build support in my kernel for this wi-fi card would be great.  (No I really don't want to use ndiswrapper)

---

### Post by GQed76 on 2006-09-19
OK I got # 3 fixed using madwifi.

any ideas on #1 and 2

---

### Post by CatKiller on 2006-09-19
If you're compiling your own kernel then you're way ahead of me. But the Ubuntu kernels include the Usplash stuff, and presumably options for modules (?) for the card and boot sector. Couldn't you just wait till the kernel that you want is in the repositories? Otherwise you're going to have to figure out the differences between the Ubuntu kernels and the kernel.org kernels and patch it yourself when you compile your own.

---

