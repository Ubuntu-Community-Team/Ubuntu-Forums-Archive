---
title: "Computer Freezing"
date: 2009-11-04
forum: Desktop Environments
---

### Post by Frugoo Scape on 2009-11-04
Every time I move a window just a little bit, the whole computer freezes. I have my ATI/AMD proprietary FGLRRX graphics driver installed and i cant think of a reason for my computer would freeze like this other then a problem with Xorg. I have also tried to reconfigure xorg using Xorg -configure and it just gives me errors saying that it can't generate a configuration. I have not done anything to the default install of Ubuntu, so I don't see a reason for something like this to be happening. I have the newest version of Ubuntu installed.

---

### Post by sphilli8 on 2009-11-04
I got a similar problem. I just upgraded from Kubuntu Jaunty (which was a total bugfest) to Karmic, and while all the little bugs seem to be gone now, there's a big one in their place. Whole system freezes within 15 or 20 minutes of booting. VERY annoying.

---

### Post by Frugoo Scape on 2009-11-04
> **sphilli8 said:**
> I got a similar problem. I just upgraded from Kubuntu Jaunty (which was a total bugfest) to Karmic, and while all the little bugs seem to be gone now, there's a big one in their place. Whole system freezes within 15 or 20 minutes of booting. VERY annoying.

Yeah, thats weird. The only difference is that I'm using ubuntu and it freezes only when I move windows sometimes. I'm not having any problems when I'm using wmii.

---

### Post by Frugoo Scape on 2009-11-04
I did some more experimenting and it can happen with only one window open. It usually happens when you try to move a window down and to the left a little.

---

### Post by Frugoo Scape on 2009-11-05
I tried using different window managers and that did not help, but then I finally uninstalled the ATI driver. It does not freeze like it did anymore, so I'm figuring that I am going to have to find a way get the ATI drivers to work correctly.

---

### Post by Frugoo Scape on 2009-11-05
After reinstalling the ATI driver, I got the problems again. I tried to reconfigure Xorg and I got a seg fault. So something is wrong with the combination of ATI FGLRX's graphics driver and Xorg.

---

