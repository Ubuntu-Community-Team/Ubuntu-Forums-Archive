---
title: "Weird display issue: i810/i815 driver issue"
date: 2006-01-07
forum: Desktop Environments
---

### Post by alamba on 2006-01-07
Hi,

I have this issue pending on my table for a while, did'nt do anything about it cos its not really effecting my work, but I would like to know what I'm missing here.

I have a HP dv 1350 laptop, I started with Ubuntu 5.04 a while ago, now, the live CD for 5.04 never did work on this system, it just brought up a blank screen. However, the install CD did work.

I got the system, up and running with no GUI initially. Then went into safemode and changed my driver to "vesa" for "i810 or i815" i think. This got the GUI up. However, native resolution was still a problem (1280x768) which I was able to fix with a couple of modeline entries into my xorg.conf.

As Ubuntu 5.10, I upgraded directly from the install CD and things have been just fine. I'm still on the vesa driver for my display.

However, the other day, I put in a Ubuntu 5.10 live CD to use gparted to make some space for a Sun Solaris installation (another thread) that I've been thinking about and I realised that the live CD booted up just fine!!

Including native resolution. I checked the xorg.conf and it was running on a i810 driver!! 

However, even now if I change my driver from "vesa" to "i810" in my installation the screen just blanks out.

Now, here are the questions:
1. Does it make any difference in performance on what driver I'm using?
2. If it makes sence, is there anyway I can move to the updated driver?

Any pointers to the who thing would be useful.

Regards,
Akshay Lamba

---

### Post by kairu0 on 2006-01-07
[QUOTE=alamba]1. Does it make any difference in performance on what driver I'm using?[/QUOTE]

Night and day.

[QUOTE=alamba]2. If it makes sence, is there anyway I can move to the updated driver?[/QUOTE]

Let's check to make sure that it's going for the right resolution. I'm running 1280x800 at 24-bit on the same chip. Is that what your /etc/X11/xorg.conf says?

---

### Post by alamba on 2006-01-25
Mine's running on 1280x768. It does say that in xorg.conf too but that's cos I manually put that in there. Including the modeline entry.

Akshay

---

