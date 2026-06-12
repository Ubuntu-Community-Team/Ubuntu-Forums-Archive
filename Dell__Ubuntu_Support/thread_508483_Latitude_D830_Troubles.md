---
title: "Latitude D830 Troubles"
date: 2007-07-24
forum: Dell  Ubuntu Support
---

### Post by jb1789 on 2007-07-24
Hello,

I have been using Ubuntu on a 4 year old Dell Inspiron 8600 for about 3 months with absolutely no problems. The installation went very well and all of my hardware was detected perfectly.

Since I had no problems installing, configuring, and using Ubuntu on my old laptop, I figured that I would have no problems installing it on my new Dell Latitude D830, but I was sorely mistaken. I used the Alternate CD to install a barely functional system, then I booted into safe/recovery mode and ran sudo dpkg-reconfigure xserver-xorg to change the video driver from nv (NVidia Quadro 140M) to the generic VESA driver. While I can now boot into Ubuntu and use the GUI, the display leaves a lot to be desired (i.e. the screensavers barely run; a moving window looks very funny...). Additionally, neither the wired nor the wireless (Intel Pro/Wireless 4965 abgn) connections are functional. I know that my wireless card will need to be properly configured, but Ubuntu does not even recognize it correctly. Finally, the keyboard, but not the touchpad, stopped functioning twice, but worked again after a restart.

If anyone knows how to fix any of these problems, I would really appreciate the help.  Also, does anyone know if some of these issues will be addressed in Gutsy, and if so, should I even bother trying to get Feisty working properly?

Thanks in advance.

---

### Post by mag82008 on 2007-07-24
Hi,

pls. have a look at 
[http://www.jordswart.org/kubuntu-on-dell-latitude-d830-with-intel-gpu/]("http://www.jordswart.org/kubuntu-on-dell-latitude-d830-with-intel-gpu/")

This should help. It worked for me..

Martin

---

### Post by jb1789 on 2007-07-25
Thanks for the reply, but I have the nVidia quadro 140M graphics card, not the intel integrated graphics.  I have tried updating the drivers for the card both manually and by using a program called Envy, but both of these procedures fail for one reason or another.  Also does anyone know the most reliable method of patching the Intel Pro/Wireless 4965, or would it be easier to wait for Gutsy?

Thanks

---

### Post by jb1789 on 2007-08-02
Since I cannot seem to get Ubuntu working, does anyone know of a different distribution where most of the hardware on the D830 would work without any serious tweaking?

---

### Post by Yorthegreat on 2007-08-06
Let's add another $0.02.

For your NVidia card, I would recommend installing the nvidia drivers (not nv, not vesa, but nvidia). You probably need to look for the glx packages. Last time I checked there were two different ones, so you might need to try either of those. Don't forget to change the driver in the xorg.conf to nvidia.

Concerning the wireless, I have no problems with that one. Worked out of the box. Now you might have a different card. Can't tell from the top of my head what card I have. I've also seen a couple of problems with the card itself. Booting into Windows and updating the driver (including some flash) might fix it.. But that is just an idea I have.

---

### Post by schnook9 on 2007-08-06
I have the D820 and the nvidia quadro NVS, got my video (in and out of the dock w/ twinview) running ok with the "new" nvidia drivers.   try doing an apt-get install nvidia-glx-new.  That should automatically include the nvidia-settings program, which you will use to configure.  don't use the standard configs, it'll just mess you up.  

HTH

---

### Post by jb1789 on 2007-08-06
Thanks for the reply.  I ran sudo apt-get install nvidia-glx-new and edited the xorg.conf file.  When I rebooted, the screen was black, again, so I booted into safe mode and changed back to the vesa driver.  Did I do something wrong, or is the nvidia driver just not working?

Thanks,
JB

---

### Post by static on 2007-08-06
I have a D620 and have had problems running NVidia stuff for ages. Specifically, if I try to run anything other than the 386 kernal, the the NVidia kernel module won't load.

Until I downgraded my kernel slighty from 2.6.20-16 to 2.6.20-15.

Now I can load the lowlatency kernel, get SMP mode, *and* load the Nvidia module. It seems the -16 kernel is missing a few support packages.

Wade.

---

### Post by jb1789 on 2007-08-07
I finally got my wireless card working (Intel 4965 abgn), and it even connects to a WPA secured network, but I still cannot install the nvidia drivers.  I tried some of your suggestions for installing the drivers, but each time I had to revert to the vesa driver.  Does anyone know if the nvidia Quadro 140M will be supported in Gutsy?


JB

---

### Post by flyd on 2007-08-09
Hey,

I just go a D830 with a Quadro 135M and initially had the same problem as you. I got it to work by installing the very latest drivers from nvidia, currently 100.14.11 ([http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)).

However, and this is what got me, you have to first remove all traces of the nvidia-glx package, as well as install a few things. I followed the pre-installation instructions here: [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490) and succeeded in installing a perfectly working driver.

---

### Post by jb1789 on 2007-08-10
Ever since I updated the kernel to get my wireless card working, via the guide [http://ubuntuforums.org/showthread.php?t=493095&highlight=4965](http://ubuntuforums.org/showthread.php?t=493095&highlight=4965), I can not install the latest libc-dev packages, which is preventing me from installing the nvidia driver.

---

