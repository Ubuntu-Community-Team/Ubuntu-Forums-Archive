---
title: "Nvidia Twinview - independent desktops?"
date: 2009-03-06
forum: Desktop Environments
---

### Post by whosmatt on 2009-03-06
Not sure what has changed, was using 8.04 with a 7200GS card with no problems, now i have upgraded to a new workstation with a Quadro NVS290 and when I enable Twinview I get one giant stretched desktop which I do not want.

Basically I need to be able to maximize a window and have it maximize to one or the other display, but not stretch across both.  this has to be simple, and i can slap an ATI card in my workstation, install the proprietary driver and it will do just this, but the nvidia card is stumping me.

Anyone?

thanks!

---

### Post by cybergalvez on 2009-03-06
> **whosmatt said:**
> Not sure what has changed, was using 8.04 with a 7200GS card with no problems, now i have upgraded to a new workstation with a Quadro NVS290 and when I enable Twinview I get one giant stretched desktop which I do not want.

Basically I need to be able to maximize a window and have it maximize to one or the other display, but not stretch across both.  this has to be simple, and i can slap an ATI card in my workstation, install the proprietary driver and it will do just this, but the nvidia card is stumping me.

Anyone?

thanks!

Do you have one of the screens set as the primary screen?

---

### Post by whosmatt on 2009-03-06
> **cybergalvez said:**
> Do you have one of the screens set as the primary screen?


I do -- Changing it doesn't seem to affect anything at all.  Also, the settings don't survive a reboot.

---

### Post by whosmatt on 2009-03-06
Scratch that.  I got it to work by having nvidia-settings replace rather than append the xorg.conf... that and a restart seem to fix things.

---

