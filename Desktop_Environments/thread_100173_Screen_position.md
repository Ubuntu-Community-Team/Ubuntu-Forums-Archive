---
title: "Screen position"
date: 2005-12-07
forum: Desktop Environments
---

### Post by amokoura on 2005-12-07
Hi!

# System info:
Dual boot: WinXP Pro / Ubuntu
Monitor: Dell E172FP LCD 1280x1024. Doesn't support auto-adjustment.
Graphics: Intel 82865G, integrated

# Problem: 
Different horizontal screen positions between the operating systems.

# Tried in Windows:
Checked out advanced display properties, but no screen position adjustments exist.

# Tried in Linux:
Using xvidtune (a program that adjusts screen properties), but it says "Sorry: You have requested a mode-line. That is not possible, or not supported by your hardware configuration.

# Requested solution:
Ability to position screen by software. It doesn't matter which operating system it will be used on.


Thanks.

---

### Post by ThePainter on 2005-12-07
Hi,
Dont know if this helps but I find many Linux distros have their desktop offset to the right a few mm's after installing Nvidia it seems to correct itself, although mandrake was Ok and after installing Nvidia it went offset !

---

### Post by Sokraates on 2005-12-07
[QUOTE=ThePainter]Hi,
Dont know if this helps but I find many Linux distros have their desktop offset to the right a few mm's after installing Nvidia it seems to correct itself, although mandrake was Ok and after installing Nvidia it went offset ![/QUOTE]

The same goes for ATI, though on my system only the command line shown at shutdown is offset. Desktop and startup (with Usplash) is centered correctly.

Somewhere along the line Usplash stopped working at shutdown, but I never cared to investigate.

---

### Post by amokoura on 2005-12-07
Thanks for the replies, but I have Intel's poor-featured integrated graphics card, so nVidia or ATI stuff won't help I guess..

---

### Post by Sokraates on 2005-12-07
[QUOTE=amokoura]Thanks for the replies, but I have Intel's poor-featured integrated graphics card, so nVidia or ATI stuff won't help I guess..[/QUOTE]

If I remember correctly, after installing Ubuntu (long ago) I briefly had the same problem. The offset was correct on Ubuntu but not on WinXP.

I simply set it right by using the settings on the monitor itself and since then everything works.

... if I remember correctly, that is.

---

### Post by Irtimid2001 on 2005-12-08
your drivers aren't installed, or not installed as they should be. I had the same problem a few weeks ago, it turned out to be some line in a config file that had a value that needed to be changed to "nv" instead of that value. Hope it helps

---

