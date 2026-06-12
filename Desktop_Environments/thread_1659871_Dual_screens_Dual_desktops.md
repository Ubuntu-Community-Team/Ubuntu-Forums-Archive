---
title: "Dual screens: Dual desktops?"
date: 2011-01-04
forum: Desktop Environments
---

### Post by SunnyDan on 2011-01-04
So recently i hooked up a second monitor to my laptop right above it, aka, vertically, and what I want is for the second monitor to be like a second computer, with a second compiz cube spinning independently from the one below it. I think I might be able to achieve this if I could increase the "Number of Desktops" under compiz's general options, but it won't let me. How to I enable my self to increase the number, or, how do I otherwise achieve my desired effect?

Thanks in advance.

---

### Post by mikewhatever on 2011-01-04
I think you'll need to run another instance of xserver and output it to the other monitor. Increasing the number of desktop spaces won't give you that.

---

### Post by SunnyDan on 2011-01-04
> **mikewhatever said:**
> I think you'll need to run another instance of xserver and output it to the other monitor. Increasing the number of desktop spaces won't give you that.

Thanks for clearing that up. So is using xserver a complicated process or something I can do in an hour?

---

### Post by Krytarik on 2011-01-04
I've done such a setup recently at my mum's machine. Unfortunately I can't access the xorg.conf at the moment, except of the Xinerama-option and the nvidia driver it is similar like this:
[https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen](https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen)

---

### Post by roguebuck on 2011-01-04
sounds like you want to set this up graphically? try this...

if you are using the nvidia drivers, open up the nvidia settings. find the tab that adjusts the resolution of multiple monitors. select your aux monitor, click 'configure' and select 'Separate X Screen'. NOT TwinView. Twinview does the xinerama 1 desktop, two monitor deal. separate x screen sets up a separate desktop on each monitor each with their own panels and such.

---

