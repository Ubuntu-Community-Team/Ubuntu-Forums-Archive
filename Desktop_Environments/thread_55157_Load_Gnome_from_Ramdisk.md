---
title: "Load Gnome from Ramdisk?"
date: 2005-08-07
forum: Desktop Environments
---

### Post by Mr Frosti on 2005-08-07
Because of the size of Gnome, it takes almost a full minute from the GDM login to sitting on the desktop in a ready state. I have done a lot of research into ways to speed up the boot times of my laptop, and now from power on to the GDM login screen takes less than 10 seconds (thanks to Initng more info here: [Howto Initng](http://ubuntuforums.org/showthread.php?t=37543&highlight=initng) 

The majority of the time is now the Gnome desktop starting up. I would like to keep Gnome because of its ease of use. I have tried other window managers, but none have been as comprehensive and friendly as Gnome. 

So... ramdisk support is enabled in the stock Ubuntu kernel, and is set to 16MB by default. I can increase this size if need be. I can write a script that will auto-mount and copy over all of the /usr/share/gnome* files to the device. My question is how can I change the path of GDM (or any display manager) to point to my ramdisk instead of my hard drive? Is this possible? It seems that loading into and then running from RAM would greatly improve the boot time and overall speed of Gnome.

---

