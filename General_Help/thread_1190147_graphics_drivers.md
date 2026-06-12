---
title: "graphics drivers?"
date: 2009-06-17
forum: General Help
---

### Post by Torlek42 on 2009-06-17
I'm new to ubuntu/linux. I installed 9.04, Wine, and version 180 of the graphics driver for my NVIDIA 8600M GT. I'm trying to play Steam games through Wine but the frame rate is extremely low. Even when I just have the Steam window up and try to move it or select items it is sluggish. Is this an issue with Wine or is my graphics driver not working right? I also can't play DVD's, something about not having permission. Thanks

---

### Post by kndfs3001 on 2009-06-17
Hi Torlek42,
Maybe you installed a bad version of the graphics drivers. Try going to System>Administration>Hardware Drivers, and see if your graphics card comes up.  If so, click enable, let the driver install, and then reboot.  If that doesn't do anything, then maybe it's a wine issue.  Not all Windows programs, such as games, work very well under wine.
--kndfs3001

---

### Post by lovinglinux on 2009-06-17
To increase performance of Steam games, select the game properties, then the launcher properties and add *-dxlevel 81*. This will force the game to use DirectX 8.1 instead of 9. Sometimes it helps a lot.

---

### Post by tcturner on 2009-06-17
i had issues with jaunty also. reinstalledd hardy and cleared them up. it sounds drastic but it worked. Issues: couldn"t set burn speed lower than 40x. also fspot had a hard time recognizing my digital camera.Jaunty wouldn't recognize webcam. installed ubuntu 8.04.2 and cleared every issue up. also the open source radeon drivers are mucho excellent. hope this helps.

---

### Post by murray92 on 2009-06-17
Can't help you with your games/driver problems, but if you want to play dvds install the restricted codecs.

[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

---

