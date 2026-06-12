---
title: "Steam - OpenGL GLX extension not supported by display"
date: 2014-01-26
forum: Gaming &amp; Leisure
---

### Post by sl8r4l8r on 2014-01-26
Steam has begun giving me the error ***OpenGL GLX extension not supported by display*** ever since I used ```
sudo apt-get install libgl1-mesa-glx libgl1-mesa-dev
``` to manually install libGL.so.1, which Steam told me was missing.  All the solutions to this error message have to do with Optimus, which doesn't work for me since I'm not using a laptop.

Here are my PC's specs:
Dell Optiplex 755
Intel Core 2 Duo E6750 @ 2.66GHz
2 GB DDR2 RAM
Nvidia GeForce GT 610
500 GB HDD

Can anyone help?

---

### Post by dannyboy79 on 2014-01-26
which nvidia driver are you using?

---

### Post by sl8r4l8r on 2014-01-26
I'm using the Nvidia Accelerated Graphics Driver (Version 319) that was recommended by the Additional Drivers section of the System Settings.

---

### Post by gta4lj on 2014-01-26
X Org is broken, I've never fixed an X Org successfully before, I just reinstall when this happens. The package you needed to install rather than the mesa-glx is called mesa-utils

Reinstalls don't take long and can never hurt, since it speeds up your system usually.

If you don't want to reinstall, you can try and regenerate your xorg.conf, but by installing mesa-glx, I seem to remember it deleting essential stuff, once again pointing to a reinstall.

Let me know if this helped.

---

