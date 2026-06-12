---
title: "Color Management in Ubuntu with ATI."
date: 2006-06-23
forum: Desktop Environments
---

### Post by Visceral Monkey on 2006-06-23
I have a problem. I like using Ubuntu, but the default color profile that my monitor uses (20 inch widescreen lcd) with my ATI 1900xtx is really, really DULL. I
n windows I can use the ATI control center to set my colors to be as vibrant as I want..but I can't seem to do it in Linux. I know Nvidia users have the option of a nvidia tool in linux, but there doesn't appear to be one for ATI. This is important because I dont want to set my colors via the monitor itself as I use windows for gaming and have the colors just right.

 I need something that will allow me to manage color via software in Linux with my ATI card. Anyone have some suggestions?

---

### Post by Martin Vysny on 2007-11-28
If you are using the binary driver from ATI (fglrx) then it's quite simple:

sudo apt-get install fglrx-control

then run the ATI Control Panel (it should be in System > Preferences or System > Administration if you use Gnome). However, I prefer to use opensource ati driver - xrandr 1.2 is way too cool :) (and besides, in Hardy, fglrx is not currently working very well - no offense guys, you are doing amazing job!). Is there a way to manage color profiles with opensource ati radeon driver?

---

