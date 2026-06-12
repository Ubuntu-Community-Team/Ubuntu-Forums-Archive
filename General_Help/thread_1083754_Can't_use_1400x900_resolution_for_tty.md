---
title: "Can't use 1400x900 resolution for tty"
date: 2009-03-01
forum: General Help
---

### Post by rajeshja on 2009-03-01
I've been trying to increase the resolution of my ttys (Ctrl-Alt-F[1-6]) but seem to be stuck with a lower resolution than the one my LCD monitor supports natively.

My LCD monitor supports 1400x900 natively. And I'm trying to that resolution on the ttys. I tried to use vga=868 (1400x900x32) as per the [Ubuntu Community Wiki]("https://help.ubuntu.com/community/ChangeTTYResolution") and [Wikipedia]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions"), but grub (or the kernel?) fails to use it saying mode 364 (hex of 868 ) is not available. If I press <Enter> at that point, it shows me a list of available modes, which does not go higher than 1152x864x32,

I switched to using 854 instead (x356), which is 1152x864x32.

Which means that my ttys are a little fuzzy now.

I'd like to use the full 1400x900 resolution even if it means I need to switch to a lower color depth.


My hardware -
Monitor: Viewsonic VA1912wb (1400x900 native)
Graphics card: ATI Radeon HD 2600 XT (512MB)
Device driver: xorg-driver-fglrx 8.54.3, 2:8.543-0ubuntu4.1 
ATI Catalyst Control Center ver 2.1

Catalyst seems to tell me my monitor's maximum resolution is 1400x1024. Not sure if that makes a difference to my situation. I would think the tty resolution should not be affected by what an X driver thinks.

---

### Post by rajeshja on 2009-03-01
According to Documentation/fb/vesafb.txt the limitation might be in my BIOS. Does this mean my motherboard BIOS or that of my graphics card? I'm assuming it's the motherboard. I'm using the Intel DG33FB.

How do I check the modes it supports and how do I get it to support an extra mode if at all that's possible?

---

