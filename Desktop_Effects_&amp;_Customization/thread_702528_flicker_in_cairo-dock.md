---
title: "flicker in cairo-dock"
date: 2008-02-20
forum: Desktop Effects &amp; Customization
---

### Post by alvinistic on 2008-02-20
Hi everyone,

I have tried running cairo-dock both using and not using glitz. The dock works but there is a glitch. Whenever I hover my mouse over the dock, the dock will flicker once. This happens everytime the mouse pointer enters the dock :(.

FYI, I use the deb package from BerliOS and yes, I have recompiled libcairo with --enable-glitz.

Anyone experience the same problem? Is there any fix for it?

Thanks in advance!

---

### Post by chavanak on 2008-02-20
New version of cairo-dock is out. Check that you are using it. Right click on the dock, then cairo-dock then check for updates. Then try once

---

### Post by alvinistic on 2008-02-20
Thanks for the reply, chavanak. I am using the latest version, which is version 1.5.1. Tried to update but the problem still persists. 

The flicker does not happen if auto-hide is activated though. But I don't want to hide the dock :(

---

### Post by chavanak on 2008-02-20
Even am using cairo-dock.. But not facing any problem btw I have 2 8800 cards running. what is your graphics card config? Are you having onboard card?> Because if you are having an onboard card, then there are few issues with cairo-dock.

---

### Post by alvinistic on 2008-02-20
My graphic card is GeForce FX 5200 Go. It should be quite decent, except the fact that it has only 32 MB VRAM. But anyway, it is enough to run AWN (which is supposed to be slower than cairo-dock). 

The problem is also there when I am not using hardware acceleration (without --glitz). Without this annoying flicker I may move to cairo-dock, although I have to say that awn is also very nice.

---

### Post by chavanak on 2008-02-20
Yes... FX5200 is good enough... Hmmmmm try to reinstall if not you can go to awn

---

### Post by alvinistic on 2008-02-20
I have done this in Ubuntu gutsy and arch linux, both have same problems :(. I have also tried this using Xfwm compositor, xcompmgr, and compiz.

Anyway, thanks so much for your assistance chavanak. Really appreciate it. Still hoping there'll be any fix though.

---

### Post by chavanak on 2008-02-20
I will keep looking if i find a solution will pm you...

---

### Post by alvinistic on 2008-02-21
Another information, using --glitz caused the cairo-dock to be unstable. Sometimes the panel did not rendered correctly and sometimes it just showed a grey box.

Any fix for this?

---

### Post by AtticusTheGreat on 2008-02-25
I'm actually an Arch Linux 64 user, but I wanted to mention that I'm having the same problem with cairo-dock.  I just recently installed it and every time I mouseover the whole dock flickers and jumps a little.  alvinistic, are you running at 64-bit as well?

Edit:  Other specs, Geforce 7600GT, nv opensource drivers, openbox WM (no dm), xcompmgr

---

### Post by mizu12 on 2008-05-20
Instead of xcompmgr turn on metacity's compositing manager: it solves this annoying problem. I switched it on 10 minutes ago so I cannot say anything about it's stability but xcompmgr crashed several times during a day, so I wasn't very satisfied with it. I hope metacity's compositing manager will be more stable. The only shortcomming it has is the inability to finetune the various shading/fading effects. (I've got Hardy on.)

*Edit: actually another bug exists: the gnome-session logout screen *([FONT="Fixedsys"]gnome-session-save --kill --gui[/FONT])* isn't visible. Just like with the xcompmgr..*

---

