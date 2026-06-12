---
title: "Nvidia and applications segmentation-fault"
date: 2005-09-08
forum: Desktop Environments
---

### Post by bolo on 2005-09-08
Hi to everyone,
yesterday i've installed the last version of Nvidia drivers (7676) with the .run script and i've tried it...

It works fine, but when i've started my pc, today, i had some problems:

First, the module nvidia.ko doesn't work and X does not start
        then i've reinstalled the driver and X start fine

Second, Xmms, Mplayer and kino doesn't start with error "segmentation fault".

When I've removed the nvidia module and used "nv" module in Xorg.conf all worked fine.

Can anyone help me?   ](*,) 

P.S. sorry for my bad, english   :roll:

---

### Post by bolo on 2005-09-08
Ok i'm helped myself

the solution is quick simply

With this comand install the modules precompiled for kernel 2.6.10.5 in ubuntu hoary 5.04

$ sudo apt-get install nvidia-glx

To modify the xorg.conf file with "nvidia" module and create a backup file of xorg.conf type:

$ nvidia-glx-config enable

If you want, you can install the nvidia settings panel with the command:

$ sudo apt-get install nvidia-settings


P.S. The cursor shadow option still not work....
P.S:2 thanx to OpenSkills Team [http://openskills.info/infobox.php?ID=1240](http://openskills.info/infobox.php?ID=1240)

---

