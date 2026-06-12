---
title: "Beryl/CompizFusion related system crash"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by SuicidalMonkey on 2007-08-28
Okay, so here's a new one for you guys.

I've had feisty and now gutsy on this machine.  The motherboard is a biostar 6100-M9 (nforce 410 based) and I'm using the onboard video.  I have the nvidia drivers installed just fine.  If I turn on beryl (in feisty) or compiz fusion (gutsy) the screen will garble with diagonal lines and the machine will lock hard.  

I can only imagine the video card is barfing on some setting.  Has anyone come across this before and know what I might need to add to my Xorg configuration to keep this from happening?

If I don't enable beryl or compiz fusion everything works fine.  It's frustrating, but at least I can use my machine without it.

Thanks for the help

---

### Post by SuicidalMonkey on 2007-08-29
Well, looks like I spoke too soon.  I just had everything crash up in the same manner and I am not using compiz fusion.  I guess I have a problem with the proprietary driver.  What that problem is exactly, I don't know.

Any ideas?

---

### Post by SuicidalMonkey on 2007-08-29
Well, I found a few things to try out, and it seems like disabling acpi in bios seems to do the trick (so far).  I wonder what is in the nvidia drivers that requires acpi to function as that is probably what is causing problems.

I tried disabling RenderAccel and UseEvents, but they did nothing.

---

