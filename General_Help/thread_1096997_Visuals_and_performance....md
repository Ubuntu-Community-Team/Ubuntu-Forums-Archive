---
title: "Visuals and performance..."
date: 2009-03-15
forum: General Help
---

### Post by Jedwinjim on 2009-03-15
Ola, 

Just made the switch from windows xp to ubuntu and so far I'm loving it, only issue i've had is with the visual performance. It all is much "laggier" than xp, almost like i've got a fresh install but haven't got the drivers updated - so the performance and quality feel well below par. small things like minimizing a window or opening a program take longer than they should and aren't as slick as I'm sure they should be.

I tried updating the drivers but all I got was ubuntu booting to a black screen - so I went back to whatever ubuntu comes with.

I've got 512meg ram, ati radeon 9600 pro and AMD athlon xp 2500+

any help is much appreciated,

cheers.

---

### Post by Ben_neB on 2009-03-15
I am pretty new to Linux also, but if you got to "System->Preferences->Appearance", and then select the "Visual Effects" tab, you can set the visual effects to "None", which I would assume, would speed up your performance.

---

### Post by Jedwinjim on 2009-03-15
sorry should have said, not running any effects at all. also tried activating propriatary drivers and now only boots up to a black screen, god this is frustrating...:(

---

### Post by flugh on 2009-03-15
There may be an easy, built-in preferred method for doing this, however I have found it to be simple enough doing it manually for my nVidia card. Your system is likely running in a default, no 3D/acceleration state out of the box. You need the good ATI driver. It is a proprietary driver though, so getting it bundled in the vanilla Ubuntu is a problem. You can download the driver installer from this page:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English)
I selected the Linux_x86->Radeon->9600. You will end up with a blahblah.run file after downloading. Just do a "sh blahblah.run" in the directory you save that file to, and I'm guessing you will be walked through the installation. I am making the assumption that the ATI installer runs similarly to the nVidia one I used. If it doesn't, I apologize for misleading you.

---

