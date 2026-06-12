---
title: "Ubuntu boots to black screen, HELP!"
date: 2007-12-15
forum: Desktop Environments
---

### Post by icer22x on 2007-12-15
OK, I am using 7.10, I just installed some xorg drivers for my ATI card from the Synaptics Manager. I also have a dual install with XP.

I went into Screens and Graphic in Ubuntu and set my graphics driver from the VESA universal card to the ATI fxgl (or something along those lines) and I restarted... now it gets to grub, I boot into Ubuntu only to get a black screen and nothing else.

Is there a way I can go into the recovery version from grub and fix this? I am a new Linux user, so some good help would be greatly appreciated.

Thanks.

---

### Post by staticvoid on 2007-12-15
> sudo dpkg-reconfigure xserver-xorg

then you can select your options and try again.

have you trierd using Envy to get your ATI card working?

sv

---

