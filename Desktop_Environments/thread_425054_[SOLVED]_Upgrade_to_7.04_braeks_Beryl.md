---
title: "[SOLVED] Upgrade to 7.04 braeks Beryl"
date: 2007-04-27
forum: Desktop Environments
---

### Post by seoras on 2007-04-27
I had a stable  Ubuntu 6.10 system running Beryl on Nvidia card very successfully, everything in Beryl seemed to work well.  

I then disabled Beryl and upgraded to Ubuntu 7.04 on line. The upgrade seemed to go well and everything seem to be OK until I re booted and allowed Beryl to load automatically. All the window headers have disappeared and no Beryl effects seem to be working. I changed the Window Manager back to Metacity on the Beryl toolbar and all the Gnome Metacity windows are OK. I also noticed that Compiz had been added to the choice of Window Managers? 

I have tried everything I can think of with manipulating the tools in Beryl but can't seem to figure out how to get the Window headers back either in Beryl of Compiz.

I have searched the forum and followed a few of the suggested fixes but none have worked for me and wondered if I am now at the stage of having to un-install Beryl and start again.

Any suggestions gratefully received.
Cheers

---

### Post by SaddaGocaraRupa on 2007-04-27
well, consider yourself lucky. i had to completely reinstall. 

what does beryl-manager tell you when you type it in the terminal?

---

### Post by seoras on 2007-04-27
Problem solved: found the solution here [http://ubuntuforums.org/showthread.php?t=419058](http://ubuntuforums.org/showthread.php?t=419058)

I followed the procedure sudo gedit /etc/X11/xorg.conf
then added the line Option ```
"AddARGBGLXVisuals" "True"
``` under the Device section to give:```
 Section "Device"
Identifier "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
Driver "nvidia"
Option "AddARGBGLXVisuals" "True"
EndSection
```

This did the trick in my case and Beryl seems to be back to normal.

Cheers

---

