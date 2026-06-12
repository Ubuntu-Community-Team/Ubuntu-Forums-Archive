---
title: "Ubuntu Feisty, Mupen64, and Video"
date: 2007-06-09
forum: Gaming &amp; Leisure
---

### Post by RKCole on 2007-06-09
Hello, everyone.

I recently installed Mupen64.  The program runs, and I have it configured so that my Xbox 360 controller can be used to play ROMs and such, but I cannot seem to get video support to function.  When I open a ROM, the program crashes.

I am using an nVidia GeForce FX 5500 AGP card with 256MB RAM, and I am using the restricted driver for the card (as the screen magnifier I use when doing daily tasks--not for playing games, though :) does not work well with the nvidia-glx driver.

Anyone have any ideas on how to resolve this?  I've seen other posts related to this, but there were no apparent solutions from what I saw.

Thanks for any input, everyone.

Take care.

---

### Post by Crube on 2007-06-18
My Mupen64 crashed everytime I tried to run a ROM. I solved it by adding read and write permissions to /usr/bin/mupen directory, switching from dynamic recompiler to interpreter or pure interpreter, switching from Glide64 to glN64 and now everything works perfectly.

---

