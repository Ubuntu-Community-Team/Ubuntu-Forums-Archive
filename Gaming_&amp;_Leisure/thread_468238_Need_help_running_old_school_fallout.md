---
title: "Need help running old school fallout"
date: 2007-06-08
forum: Gaming &amp; Leisure
---

### Post by CDiablo on 2007-06-08
Heres my problem folks and I have it down to a tee but dont know what to do. I have fallout fully installed to run in Wine. I run a shell script to get it to run in its own X window using this

```
#!/bin/sh
 
 X :3 -ac &   # Launches a new X session on display 3 
 cd "/home/c"   # 
 sleep 2   # Forces the system to have a break for 2 seconds 
 DISPLAY=:3 /usr/X11R6/bin/wine /home/c/.wine/drive_c/Program\ Files/Interplay/Fallout/falloutw.exe
```

Now this works fine with exception of the fact that the screen is off center as if 1/4 of the the game goes past where the screens border is. I know that the problem is that I run 640x480 @59htz by default. I need the screen to default to 640x480 @76 htz. Is there anyway to force this in the shell script or in the xorg.conf file. Thanks for the help all.

---

### Post by Spirale23 on 2008-07-05
did someone manage to run fallout with ubuntu ppc on a powerbook ???

---

