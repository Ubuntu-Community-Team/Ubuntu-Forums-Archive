---
title: "Resolution Blues"
date: 2007-11-29
forum: Desktop Effects &amp; Customization
---

### Post by XtremeRadiation on 2007-11-29
I have AMD 64 running at 1.8 Ghz, 1 GB RAM, 120 GB HDD. I have a ATI Radeon Xpress 200 128 MB in-bulit on the motherboard. My monitor is Samsung Syncmaster 798 MB 17-inch (CRT). I have Windows Vista Home Premium also installed.

I recently installed Ubuntu 7.10 (64-bit). But the thing is that its not recognising my monitor nor my gfx card. The maximum resolution I can have is 600x400. I tried changing resolutions but it just doesnt change from 600x400. No can i turn on the desktop effects even though i have a 128 mb gfx card.

---

### Post by Takster on 2007-11-29
Have you installed ATI drivers?

maybe in /etc/X11/xorg.conf

> Section "Device"
Driver "ati"

"ati" should maybe be "fglrx" or "radeon".

Can you post your config file? :)

and also;type: **fglrxinfo**
in terminal, see what you get.

> tak@Ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7059 Release


---

