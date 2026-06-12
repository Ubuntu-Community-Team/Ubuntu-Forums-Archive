---
title: "Blank screen on shutdown/restart/end session"
date: 2006-06-02
forum: Desktop Environments
---

### Post by wayanwolvie on 2006-06-02
Hi, I got this strange problem with my Kubuntu (I use Dapper final release). Everytime I choose to end current session or shutdown my computer, it returns blank screen (after the "log-off" sound). And if I wait a bit longer, my LCD LED will be blinking (as there is no output). But my CPU is still on. Can anyone help me please?

---

### Post by hippyjim on 2006-06-02
Me also!

Although Dapper looks gorgeous this is a bit worrying.

---

### Post by hippyjim on 2006-06-17
~bump~

Anyone fix this yet? I have to keep cutting power to my motherboard to shut down - surely it's not good for it?

---

### Post by rumli on 2006-06-17
See [this post]("http://ubuntuforums.org/showthread.php?p=1150408#post1150408").  I had a similar problem with Ubuntu.

---

### Post by raptros-v76 on 2006-06-17
first:
sudo aptitude install svgalib
then edit /boot/grub/menu.lst to have vga=791 for each of the boot entries, and also in the default options

---

### Post by wayanwolvie on 2006-07-31
It's not work on my Kubuntu. The problem is still there.

I think the problem is on the nvidia driver. If I activate the driver (changing the "nv" to "nvidia" on xorg.conf), I got the problem. But if I  change back the xorg.conf, the problem is missing, but I can't use the 3D accelerator (openGL) :confused: :confused: :confused:

---

