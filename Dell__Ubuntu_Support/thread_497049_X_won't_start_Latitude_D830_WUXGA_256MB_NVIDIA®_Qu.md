---
title: "X won't start: Latitude D830 WUXGA 256MB NVIDIA® Quadro NVS 140M"
date: 2007-07-09
forum: Dell  Ubuntu Support
---

### Post by tewk on 2007-07-09
I've got a:

Latitude D830   	  
Intel® Core™ 2 Duo T7500 (2.20GHz) 4M L2 Cache, 800Mhz Dual Core
LCDs 	15.4 inch Wide Screen WUXGA LCD Panel
Graphics 	256MB NVIDIA® Quadro NVS 140M™

X works great with vesa and 1280x1024 resolution, but I can't get the nv driver to work at any resolution.

I'll I do is switch vesa to nv and I get 
(EE) No display device found.
(EE) Screens found, but no suitable display found.

Ideas?

---

### Post by jjfraney on 2007-07-10
I have almost the same system.  Same video card on a D830 anyway.

I found this page: [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

I would like to tell you how I did with it, but I cannot read my cdrom!

Regards,
John

---

### Post by jjfraney on 2007-07-10
Just a follow up.  I installed the driver successfully using the instructions of my previous post.

Regards,
John

---

### Post by Flopy on 2007-07-14
I have the same laptop and I got it to work like this:
I used the 64-bit Alternate and installed only the command line system, from there I installed 'ubuntu-desktop' and when done, instead of restarting, I changed /etc/X11/xorg.con to use the 'vesa' driver instead of 'nv'. This was all done through the command prompt (no X yet)

restart.

Now i have ubuntu in graphical mode, and proceeded to use these instructions: [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)
> Debian GNU/Linux or [K]Ubuntu with Xorg 7.x

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    rm -f /lib/linux-restricted-modules/.nvidia_new_installed

After that I used the Envy script to install the nvidia driver.

Note that any time you upgrade your kernel, you probably want to change back to the vesa driver before restarting into a blank environment (as then you'll be working blind -- happened to me and had to trust my instincts to edit xorg.conf). Restart and use the Envy script again and you're good to go! :)

-Victor.

edit: the Envy script can be found here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

