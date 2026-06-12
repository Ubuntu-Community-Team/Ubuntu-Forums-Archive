---
title: "Kernel Update leads a problem?"
date: 2008-01-24
forum: Desktop Environments
---

### Post by incen on 2008-01-24
Hi,

There was a notice that new updates were available yesterday, so I updated my Ubuntu 7.04, Feisty Fawn, on my desktop. However, I reboot my computer this morning, but it froze while running the loading bar (freezing when the third grid full). I tried to reboot again and obviously the kernel got updated to 2.6.20-16-generic! Before, mine is 2.6.20-15-generic. After the second boot, it froze at the same part. Now, I can boot into 2.6.20-15 without any problem. But please help me to solve the 16-generic problem. Thanks!

---

### Post by PmDematagoda on 2008-01-24
When you boot into the Recovery Mode of the new kernel do you get any errors?

---

### Post by incen on 2008-01-24
Hi, thanks for giving me some idea. I'm new to Linux.
Now I'm trying to boot in recovery mode.
First time, it ran through quickly on the black/white mode and I couldn't really got to see what error there might be. And then, it seems it jumps back to reboot again and then I got to boot loader again. So I pick 16-generic (recovery) again. Now, it stops at:

* Loading hardware drivers...
r8169: eth0: link up
r8169: eth0: link up
agpgart: Detected an Intel G33 Chipset.
BUG: at lib/kerf.c:32 kref_get()

Call Trace:

So I think the problem happened at lib/kerf.c:32 kref_get(), right?
But how to fix it?

Thanks!

---

### Post by metalheart on 2008-01-24
Try to disable Intel graphics module. Write

```
blacklist i810
```

to the end of /etc/modprobe.d/blacklist file and reboot (I hope the module name is correct).

How do you installed the graphics driver? From Ubuntu repository or compiled from source? For the latter you may need to build them again for this kernel. Then remove the module from blacklist.

---

### Post by incen on 2008-01-24
I built my computer in Sep last year. I put Windows XP on my machine first and then put Ubuntu 7.04 on after. Then everything worked fine until I made those updates. Now I just downloaded 7.10 and will try to install it on my machine later on. I think this is probably a easiest way since I don't have much stuff on my machine yet.

---

