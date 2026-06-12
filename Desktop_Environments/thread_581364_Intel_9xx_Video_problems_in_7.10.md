---
title: "Intel 9xx Video problems in 7.10"
date: 2007-10-19
forum: Desktop Environments
---

### Post by sxturbo on 2007-10-19
After installing 7.10, my Intel 9.x driver is not working. I get generic resolutions offered to me. 1600x1200, 1280x1024, etc. 

I'm running a Intel 9 series videocard on a dell GX620 with a 24" widescreen monitor. Everything was working fine in 7.04...upgrade killed it.

I reinstalled through the package manager the the appropriate 'xserver.xorg' file for the intel 8/9 series...along with the 915 resolution fix. Still no go.

any ideas guys?

---

### Post by tschneiter on 2007-10-19
For me, installing xserv-xorg-video-intel and then doing: sudo dpkg-reconfigure -phigh xserver-xorg was enough to get my card working.

---

### Post by dietrying on 2007-10-19
i also had problems with my intel 945 integrated graphics card on gutsy. Especially switching to vga-out (for beamer) with fn+F4 didn't work the way it used to in feisty. But that was not the only problem. if i set the screen with the graphic tool to 1280x800 (wich is my screen resolution), i owas only able to get resolutions 1024x768 and 800x600- strange!!!

Most of my problems where solved by setting the driver back (from intel to i810) wich works very well on my subnotebook (samsong q35 ceron). After that everything works good.....

David:guitar:

---

### Post by e1_ang on 2007-10-30
Same experience in Ubuntu 7.10.

My notebook is Samsung Q35

---

### Post by trappist on 2007-11-14
In Gutsy I had to "downgrade" my driver from "intel" to "i810", and use 915resolution to hack the widescreen resolution in.

---

