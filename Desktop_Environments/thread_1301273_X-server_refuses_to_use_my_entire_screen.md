---
title: "X-server refuses to use my entire screen"
date: 2009-10-25
forum: Desktop Environments
---

### Post by gorcq on 2009-10-25
I have a Toshiba Portege 3500 tablet pc with a trident video card. I was running ubuntu gutsy on it but have just now upgraded to jaunty. Originally, the highest display resolution available to me was 800x600, despite that I am used to 1024x786, and this would appear as a small rectangle in the middle of the screen having an inch or so wide black border around it.

The file /etc/X11/xorg.conf was originally empty. Following the advice of some website or other, I attempted to fix the problem described above by adding the following to that file:
```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 1024 768
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection
```
After restarting the computer, I am now able to select 1024x768 as an option in the display menu, and the system will generate a desktop of that size. However, it still appears inside an 800x600-pixel area in the middle of the screen having black borders of an inch or so wide. The entire desktop is never visible at one time: the bottom and the right side start out "off-screen," for lack of a better word. If I attempt to move the mouse past the edge of the rectangle I've described on the right side or the bottom, the desktop will slide over so that I can see a different portion of the larger area. I hope that description is understandable.

I am not certain what exactly is causing this, but any help with it would be appreciated.

Edit: Seems I missed a thread on this site that has the solution. Never mind.

---

### Post by svaens on 2009-11-02
hey! Which thread did you find? Help your fellow ubuntu users mate! I have a similar problem.

---

