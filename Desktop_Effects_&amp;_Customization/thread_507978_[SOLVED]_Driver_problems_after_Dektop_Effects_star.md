---
title: "[SOLVED] Driver problems after Dektop Effects start"
date: 2007-07-23
forum: Desktop Effects &amp; Customization
---

### Post by memm74 on 2007-07-23
Hello,

I recently installed Ubuntu 7.04 on a five year old Toshiba laptop. Everything was working well until I started Desktop effects for the first time. The system installed some nVidia drivers and since then I can't use the system anymore, because the screen stays black after the system booted.. (when you should see the log in screen).

Is there an easy way of undoing the installation of the last installed rivers that cause this problem?

Best wishes

Matt

---

### Post by memm74 on 2007-07-24
I tried to fix this problem. The first idea was to uninstall those drivers...

In recovery mode I checked for installed packages using

dpkg -&#8211;get-selections 

Two nvidia packages were listed

nvidia-glx
nvidia-kernel-common

I removed the first one

apt-get remove nvidia-glx

After restarting the machine I got an error message 

failed to start the X server

so I reinstalled nvidia-glx

apt-get install nvidia-glx

Now I am back to square one..

Does anybody know how to disable Desktop effects? (from the shell as I can't log in anymore)

---

### Post by memm74 on 2007-07-25
It works now after I used the xorg.conf from the Live CD. (drivers without 3d support?)

To get the drivers for 3d effects working I followed the instructions from this forum
[http://www.nvnews.net/vbulletin/showthread.php?t=84773](http://www.nvnews.net/vbulletin/showthread.php?t=84773)

---

