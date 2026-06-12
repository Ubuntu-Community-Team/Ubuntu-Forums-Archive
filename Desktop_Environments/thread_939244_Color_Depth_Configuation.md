---
title: "Color Depth Configuation"
date: 2008-10-05
forum: Desktop Environments
---

### Post by Kilmarac on 2008-10-05
Ok, I have some programs that require a 32 bit color depth.  However, everytime I change the xorg.conf, gnome defaults to a "low level" resolution to allow me to configure the dispplay. 

Hardware is

NVIDIA geforce 7300
Viewsonic vg2021 Display

My xorg.conf section for the device and monitor looks like 

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

```

I change DefaultDepth to 32 and it breaks.  What am I doing wrong?

---

### Post by rozbarwinek on 2008-10-06
There is no "32 bit" colour in Linux :)
24 bit in Linux = 32 bit in windows :D

---

### Post by mcduck on 2008-10-06
The thing is that 24-bit colors _are_ as much as you'd want. That's 8 bits per color channel, 3*8=24.

32-bit colors would mean 24 bits for colors + additional 8 bit alpha channel for transparency. Since displays don't have transparency the alpha channel doesnt really do anything here.

Windows just happens to refer to 32-bit colors even when they really mean 24-bit colors.

(of course 32-bit images are also really used, but not for your display. The alpha channel is composited with whatever is behind the picture to create 24-bit image that your display can handle. And the alpha chanel isn't a color channel anyway..)

---

### Post by Kilmarac on 2008-10-06
Hrm... thats strange then, why would a program for linux fail then and the message log say something about needing 32bit colors.   Ok, Ill got post the problem in that forum. 

Thanks

---

### Post by EnGorDiaz on 2008-10-06
> **Kilmarac said:**
> Hrm... thats strange then, why would a program for linux fail then and the message log say something about needing 32bit colors.   Ok, Ill got post the problem in that forum. 

Thanks

bcus i guess the programmers smoke pot

---

