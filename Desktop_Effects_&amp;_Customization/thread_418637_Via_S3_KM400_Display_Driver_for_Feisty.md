---
title: "Via S3 KM400 Display Driver for Feisty"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by jayflower on 2007-04-22
Do I have to install de unichrome drivers for my [FONT="Comic Sans MS"][COLOR="Orange"]graphic chip[/COLOR][/FONT] in Feisty? I ask becouse I want to try 3D and I couldn't with Edgy. I wish this time will be easier, of course, 3D is Beryl.
Thanks in advance

---

### Post by stephanvaningen on 2007-04-29
I tried with installing the package xserver-xorg-video-unichrome using the Synaptic Package Manager (it suggested to remove these packages: xserver-xorg-video-all, xserver-xorg-video-via which I did).
After restart X did not work again and I had to install the removed and remove the installed again (using command-line apt-get). 
But I'ld expect that this package (xserver-xorg-video-unichrome) must be the package I need: ?

---

### Post by nayk on 2007-05-02
When I installed Feisty on my AMD VIA desktop, I got the right screen resolution 1024/768 at 85MHz however, the monitor kept blinking every so often. Eventually, I installed  xserver-xorg-video-unichrome through Synaptic and like stephanvaningen said above, it asked me to uninstall two other via drivers. Well I did it; restarted my computer... and now the computer monitor is not blinking. Maybe it has worked on my system. Desktop effects still do not work, but at least the blinking has stopped.

---

### Post by wezlo on 2007-05-08
Any time I use the via or unichrome drivers, I can't use X at all - it slows down the system to a crawl...

---

