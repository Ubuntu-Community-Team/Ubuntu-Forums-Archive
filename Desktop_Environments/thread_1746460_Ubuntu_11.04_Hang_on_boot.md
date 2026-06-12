---
title: "Ubuntu 11.04 Hang on boot"
date: 2011-05-01
forum: Desktop Environments
---

### Post by szetheli on 2011-05-01
I'm hoping someone here can give me steps to further debug this problem, or at least point me to related bugs.

I've had a home built HTPC that was working well under Ubuntu 9.10 (64 bit).  I've tried a fresh install of 11.04 (64 bit) and its hanging at various parts of the boot.  

Here's what I've tried:
**Normal boot: **
results in a hang with either black background and an unmovable mouse pointer, or the ubuntu default background with an unmovable mouse pointer.  At some points during the boot the mouse pointer will move, but then the screen will flicker and come back with it frozen.

**Recovery boot: **
hangs ubuntu logo with the console output it was showing up to that point squished and repeated three times across the top of the screen.  No sign of a console to type into.

**Modified boot options, in various combinations**: apparmor=0 noapci vga=773 
no difference from above.

**Memory Test:**
No errors

**Hardware:**
Hauppauge 1800 card - currently unplugged while I try to identify what's failing
Motherboard - ASUS M2NBP-VM with built in NVIDIA GeForce 6 GPU
6 GB RAM
DVI out to Toshiba HD TV (9.10 had no problems driving 1920x1080)

Anyone have pointers on what I can do to at least debug what is causing the hang/crash?  As it is I can't get to a terminal to even look at dmesg or syslog.
I can get to the grub terminal, but I'm not knowledgeable enough to emulate a step by step boot without a how-to guide.

---

