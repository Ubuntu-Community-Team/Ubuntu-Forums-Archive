---
title: "GRUB2 does't load after 10.04 x64 install on Dell Precision T5500n"
date: 2010-12-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fr4ncium on 2010-12-03
Hi all,

I'm trying to install Ubuntu 10.04 64-bit on a Dell Precision T5500n. I tried an install from a live CD and from the alternate installer later on. The install process both times went smoothly and I used the entire harddrive. However, when I try to boot the machine, it goes past the BIOS splash screen, shows a blinking underscore for a short bit, then the screen says there is no input signal. GRUB2 is never loaded. Could you guys help me figure out what is going on? Thanks!

OK This is solved now. Turns out GRUB2 was loading (I thought it would show up even with a single boot system, but I was wrong) and something involving the video drivers for the QUADRO in the system made it crash or something. Which is strange because I could run the live CD and use the default installer with X11 just fine, which was not the case in the last 10.04 machine with gpu driver problems (had to use the alternate install disk).

---

