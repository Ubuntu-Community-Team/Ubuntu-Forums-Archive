---
title: "Ubuntu Splash Screen"
date: 2011-01-21
forum: Desktop Environments
---

### Post by RyanMcD86 on 2011-01-21
Hi, im trying to change my splash screen. i followed this tutorial 

[http://joesteiger.com/2011/01/14/change-boot-screen-plymouth-theme-ubuntu-10-10/](http://joesteiger.com/2011/01/14/change-boot-screen-plymouth-theme-ubuntu-10-10/)

Now I'm stuck. Not sure why.. however it wont change and i just keep getting the basic font splash screen where it just looks generic. Anyone know why it its the basic splash screen? Any help would be great. thanks :D

---

### Post by andymorton on 2011-01-21
I always do it just using the terminal, without any GUI tool. Plymouth themes usually come with a readme file which gives the commands you need to enter. 

e.g. [http://www.n00bsonubuntu.net/content/ubuntu-orange-plymouth-theme-for-ubuntu-10-04-lts-lucid-lynx/](http://www.n00bsonubuntu.net/content/ubuntu-orange-plymouth-theme-for-ubuntu-10-04-lts-lucid-lynx/)

The instruction are there on the site. I usually get them from gnome look but it doesn't seem to be working at the moment. 

andy

p.s. you can also get some plymouth themes from the synaptic package manager. When you've installed them open a terminal and enter  - 'sudo update-alternatives --config default.plymouth' to choose between them. Just enter the number which corresponds to the one you want.
When you've done that enter 'sudo update-initramfs -u'. And you're done.

---

### Post by Krytarik on 2011-01-22
> **RyanMcD86 said:**
> 
Now I'm stuck. Not sure why.. however it wont change and i just keep getting the basic font splash screen where it just looks generic. Anyone know why it its the basic splash screen?
It seems like you're talking about the text only, non-graphical, splash screen.
It occurs sometimes by using the proprietary video drivers of AMD/ATI and Nvidia.
Try this workarounds, from the plymouth readme (/usr/share/doc/plymouth/README.Debian):
> High-color graphics on nVidia, ATI and other cards
--------------------------------------------------

Our default configuration uses low-color graphics on cards or drivers
for which "Kernel Mode Setting" (in-kernel graphics drivers) are not
available.

This is because the driver that permits high-color graphics tends to
cause issues with suspend and resume, and we opted to prefer that
working.

    For nVidia and ATI users, the default "nouveau" and "radeon"
    drivers are Kernel Mode Setting enabled, but do not always
    provide 3D capability at the current time.  By switching to
    using the restricted/non-free nvidia-glx or fglrx drivers,
    you will gain 3D capability at the loss of a high-color
    splash screen.

You can however chose to enable high-color (and resolution) console
if you find it doesn't affect suspend/resume for you, or you don't
use that feature.

There are various methods of doing this, the most robust is the
following four steps:

 Append video=vesafb to the GRUB_CMDLINE_LINUX_DEFAULT in
   /etc/default/grub
 sudo update-grub

 echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
 sudo update-initramfs -u

---

### Post by RyanMcD86 on 2011-01-24
Thanks for the help guy's. I guess some of the boot screens are not compatible with Ubuntu 10.10. some of them work. and some don't. But thanks for all the help.

---

