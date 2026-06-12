---
title: "plz help before i break my ubuntu again lol"
date: 2009-11-05
forum: Desktop Environments
---

### Post by Steve60938 on 2009-11-05
I wanted a few of the cooler effects and looks on my pc so i followed a few tutorials i did the emerald --replace thing and tried to use the 3d desktop cube and now not only do i not have the cube i only have 2 desktops even tho theres four squares at the bottom of my screen. the desktop does rotate but is more like a peice of flat paper than anything and i also dont know how to get back to compiz from emerald i tried to do compiz --replace and it gave me this output: 

steve@steve-desktop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
  





its been running for about 10 mins and when i went to close the window it told me not to cause something is using it.

---

### Post by Amgad elsaiegh on 2009-11-06
no body got a clue ??

---

### Post by realzippy on 2009-11-06
your desktop cube has only 2 desktops.You change it in ccsm
(compizconfigsettingsmanager).

system/preferences/ccsm/general options/desktop size

set slider to 4 desktops.


emerald is a windowborder decorator for compiz.To get it run when compiz starts,open ccsm/window decorator/ and insert in "command":

emerald --replace

To start compiz.
rightclick on desktop,last option,visual effects

---

### Post by Steve60938 on 2009-11-06
oh ok so enabling emerald didnt get rid of compiz or what was there to begin with...whew lol. and I figured out the cube thing what i dont understand is how come theres no desktop on the top or bottom of it....not really a cube then...

---

