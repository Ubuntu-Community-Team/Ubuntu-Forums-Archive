---
title: "Error, NO glx visuals"
date: 2007-04-19
forum: Desktop Environments
---

### Post by plinny on 2007-04-19
Hello everybody:)
     I'm pretty new at all this stuff, and think I bit off more than I can chew!  While trying to install Xgl, I managed to screw up my xorg.  So I reconfigured it.  The display worked.  Then, while trying a different approach to installing Xgl, I messed with the gmd.  That's when I got no display, just the command line. So I tried to reconfigure that (the gmd)....but still no graphics.  The readout I got says that although I have an Intel graphics card, it's trying to use the Nvidia driver!  (i think i installed it before i figured out that beryl will work with i810, my driver).  Also, I keep getting the error No GLX visuals.  Any help you can provide would be great!
    Thanks, 
        plinny
 P.S. I'm running Fiesty Fawn on an emachine laptop with AMD Athlon card

---

### Post by Theimon on 2007-04-21
Try adding ```
[SIZE=-1]Option "**AddARGBGLXVisuals**" "True"
``` to the Device section of your xorg.conf and restart the X server.
[/SIZE]

---

