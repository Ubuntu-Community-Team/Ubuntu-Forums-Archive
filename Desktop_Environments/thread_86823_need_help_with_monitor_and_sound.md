---
title: "need help with monitor and sound"
date: 2005-11-06
forum: Desktop Environments
---

### Post by cooldudejz on 2005-11-06
i recently did a fresh install of breezy. everything is working great, but my monitor and sound card. i know these are easy fixes but i am to new to linux to fix the problems myself.
my monitor is stuck on a resolution of 800x600. i dont know how to change it and going to system->preferences->screen resolution, does nothing, i think i need to change something in my xorg
second i have a very old sound card a sound blaster sb 32, i cant get it to work also.
any help is greatly appreciated.

---

### Post by Ampersand on 2005-11-06
Running 
```
sudo dpkg-reconfigure xserver-xorg
```
should give you the option to select more resolutions.

If this doesn't work, run
```
sudo gedit /etc/X11/xorg.conf
```
scroll down to Section "Screen" at the end, and add the resolutions your monitor's capable of on each of the lines starting 'mode'. For example:
```

Depth               1
Modes              "1024x768"         "800x600"       "640x480" 

```
(repeat for each colour depth).

---

