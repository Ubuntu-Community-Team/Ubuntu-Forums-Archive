---
title: "Compiz Effects + Nvidia 8600gt = Xserver Failure"
date: 2008-02-28
forum: Desktop Effects &amp; Customization
---

### Post by DJPlayer on 2008-02-28
usually I tend to just look up info myself and fix.. which I've done.. but I'm up to about the 10th time now..

I've been through my xserver config file many times now.. I'm always changing it from vesa to nv.  Then "normally it works".

I have then noticed the driver is on the unsupported list and have to enable it.  that will usually fix my problems.. usually w/ a little tinkering..  

but then I go to turn on the compiz effects. (currently they are set to lowest setting."  tells me that I can't.. then I try again..  and it seems to accept and prompts for the reboot.. 

next boot.. xserver fails.. it always seems to mention not finding the Nvidia driver if you look through the xserver log.  

please.. help.. I once had the effects going and I really want them back.  btw. my video card is a 8600gt

---

### Post by -random on 2008-02-28
do you run ubuntu 32bit?

If so, here's what i did: [http://ubuntuforums.org/showthread.php?p=4410729#post4410729](http://ubuntuforums.org/showthread.php?p=4410729#post4410729)

---

### Post by Therion on 2008-02-28
Install and run [Envy](http://albertomilone.com/nvidia_scripts1.html).

Very possibly, once it's done, you'll need to enable the restricted driver and configure xorg.conf but ONLY to change the screen resolution to what you want to use; that's it.

Compiiz should allow you to use all the advanced features at this point.

---

### Post by DJPlayer on 2008-02-28
> **Therion said:**
> Install and run [Envy](http://albertomilone.com/nvidia_scripts1.html).

Very possibly, once it's done, you'll need to enable the restricted driver and configure xorg.conf but ONLY to change the screen resolution to what you want to use; that's it.

Compiiz should allow you to use all the advanced features at this point.

i've ran envy a number of times.. it fixes the problems w/ the xserver error.. but it still doesn't allow me to use the compiz effects.  I think I might use envy and then run the setup for xserver over again making sure to use all default settings..  I'm unsure what screen resoluction to use those for the xserver.. last time I went very conservative, I think 800x600 on my 22' widescreen.

---

### Post by DJPlayer on 2008-02-28
this is my xserver.conf modifying again..  the driver for video loves to swap back to vesa

Section "Device"
        Identifier      "nVidia Corporation G80 [GeForce 8600 GT]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G80 [GeForce 8600 GT]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

---

### Post by Therion on 2008-02-28
> **DJPlayer said:**
> i've ran envy a number of times.. it fixes the problems w/ the xserver error.. but it still doesn't allow me to use the compiz effects.  I think I might use envy and then run the setup for xserver over again making sure to use all default settings..  I'm unsure what screen resoluction to use those for the xserver.. last time I went very conservative, I think 800x600 on my 22' widescreen.
Use Envy, enable the driver through Restricted Driver Manager, then configure xorg.conf to use the nVidia (not vesa, not nv,) driver and configure your screen resolution.  Take the defaults in xorg.conf everywhere else.

---

### Post by dark_phantom on 2008-02-28
I had problems with my 8800, so I tried a few things and now it's working.  I installed envy, install the nvidia drivers then sudo dpkg-reconfigure -phigh xserver-xorg, restart X.  Reinstall the nvidia drivers with envy.  I don't know exactly what did it but it seems the reconfiguration of xserver was what helped.

---

