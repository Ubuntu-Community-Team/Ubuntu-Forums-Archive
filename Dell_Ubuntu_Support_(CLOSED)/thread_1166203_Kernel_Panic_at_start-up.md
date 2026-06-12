---
title: "Kernel Panic at start-up"
date: 2009-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Humanities Major on 2009-05-21
Hi, I have Ubuntu, hardy version installed on an Inspiron 1420 and I was in the middle of installing updates (not a version upgrade, just normal updates) when the whole system froze and all the cap locl, etc lights started blinking.  I left it for 15 minutes or so then, since I could not do anything, shut it down and restarted it.  When it restarted (and every restart since)it says 
[   9.156075] kernel panic - not syncing: VFS: Unable to mount root fs on unknown wn-block(0-0)

This is right at startup before grub so I can not even go back and reset it to factory original settings.  Does anyone have any ideas?

---

### Post by Humanities Major on 2009-05-21
I was able to restart while holding down the fn key (that is hold down the power and fn key until you enter diagnostic mode), the diagnostic did not really help, but after exiting I briefly got the GRUB screen, from which I could run a previous version of the kernel and now it works fine.

---

