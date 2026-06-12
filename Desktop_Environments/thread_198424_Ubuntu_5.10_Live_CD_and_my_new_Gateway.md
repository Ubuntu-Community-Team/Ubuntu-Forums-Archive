---
title: "Ubuntu 5.10 Live CD and my new Gateway"
date: 2006-06-17
forum: Desktop Environments
---

### Post by bl@ckm@ge987 on 2006-06-17
Hi, I'm having problems using the Ubuntu 5.10 Live CD on my new Gateway computer, it all goes good, until:
"Failed to start the X server (your graphical interface) It is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem?"

I press Enter, and then...
It goes through some [ok] things, then gets to "*checking battery state...." and nothing happens.

Is it simply that my specs aren't supported?

I have a Gateway (GT5056)
AMD Athlon 64 X2 Processor 3800+
vVidia GeForce 6100 GPU
1024MB DDR

Also, is it possible to install Ubuntu along with Windows XP on the same HDD without need ing to alter the partition and risk losing my data?

---

### Post by jtwJGuevara on 2006-06-17
Hello,

I'm guessing that, for whatever reason, the driver referenced in /etc/X11/xorg.conf is either the wrong driver or it is the right driver, but its module is not being loaded.  Unfortunately, with the LiveCD, I know of no good way to remedy that on the fly.

To answer your harddrive partition question, if you have only one harddrive presently, and that harddrive has exactly one partition that takes up all of the harddrive space, then there isn't any convenient way to install two OS's on your machine without first formatting your harddrive - which completely obliterates your Windows partition.  I'm not keen on what types of tricks that might exist to install OS's on the same partition, but to my knowledge, it isn't possible.

---

### Post by bl@ckm@ge987 on 2006-06-17
Ok thanks, is it possible to rip the .ISO, and extract it to edit the xorg.conf, then burn it again? I have the software to do it.

---

### Post by jtwJGuevara on 2006-06-17
I'd say its worth a shot just to see what xorg.conf has listed as its video driver.  Is there anyway you can get to the command line after your X server fails on the live CD itself?  Also, if you can get to a command prompt from your live CD type the following:

```
lsmod | grep nv
```

This should return any nvidia drivers (if any) that were loaded.

If you discover something it won't hurt to edit that .iso file and burn a new cd again... the only thing you risk losing is a cd which can be converted to another coaster :)

---

