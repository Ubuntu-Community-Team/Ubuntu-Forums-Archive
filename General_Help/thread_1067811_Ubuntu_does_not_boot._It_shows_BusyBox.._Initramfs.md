---
title: "Ubuntu does not boot. It shows BusyBox.. Initramfs"
date: 2009-02-12
forum: General Help
---

### Post by the_analyzer on 2009-02-12
I recently reinstalled ubuntu, (I had 7.04 and it worked fine) 
I installed now 8.04, and after the first installation It was fine, I also put my documents.

But now when I restart and I choose ubuntu (I also have vista, in the other hard drive)it shows

```
BusyBox v1.1.3 (Debian 1:1 3-5ubuntu12)..
Enter 'help' for a list of built-in commands.
(initramfs)
```

---

### Post by LowSky on 2009-02-12
It might sound weird but check the cables to your hard drives and DVD drive. make sure you use 80 pin IDE cable over the 40 Pin cables.

I had this issue too when upgrading from to 8.04. Something changed in Ubuntu kernel or something where I couldn't no longer use my DVD-ROM drive to Rip music or play music since 7.10,  but I had not  seen the busybox issue until 8.04(oddest thing as Windows seemd fine), it turned out to be the cable. When I was trying to diagnose the issue it turned out to be a simple cable switch.

---

