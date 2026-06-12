---
title: "Deus Ex with wine fullscreen"
date: 2007-01-04
forum: Gaming &amp; Leisure
---

### Post by JPMaximilian on 2007-01-04
How can I get Deus Ex to run fullscreen?  I installed wine with automatix, installed the deus ex demo, and the game runs fine, but only windowed.  This wouldn't be so bad, but the game is kind of dark (not because of ubuntu, its a dark game), so, having a bright desktop with light menu bars around is somewhat annoying.  Ideas?

---

### Post by JPMaximilian on 2007-01-04
OK, so i tweaked the setting in winecfg, under the graphics tab i just unchecked everything besides the direct 3d part.

---

### Post by JPMaximilian on 2007-01-04
Two other issues I have, is there a way to use hardware acceleration in wine?  If I install proprietary ati drivers for gnome will that work in wine?  Also, my keyboard doesn't work in deus ex when running fullscreen.

---

### Post by Enverex on 2007-01-10
Yes, if you have Hardware accelleration working in Linux itself then Wine will use it.

There are two possible reasons for Deus Ex running "windowed". First is because you've set Wine to use a Virtual Desktop in "winecfg". If not then it's XOrg going funky because you don't have the screenmode available that the game is trying to use. In a terminal check "xrandr" and that it lists the screenmode the game uses. If not then you need to add it to the "Modes" at the bottom of your xorg.conf file (if a mode isn't available then it picks something close and uses as much of that screen as it can). A big issue here is the nVidia drivers bundled with Ubuntu at the moment. They are very broken. EDID (the thing that talks to the monitor to see what modes should be available) doesn't work so you only have the max available. Someone on the Ubuntu team needs to update the drivers...

---

### Post by JPMaximilian on 2007-01-10
I know why it runs windowed, and the screen mode I'm trying to use shows up when I run xrandr, but why doesn't my keyboard work when I run the game fullscreen.  I have an ATI video card, so nvidia drivers couldn't be an issue.

---

### Post by Enverex on 2007-01-11
Make sure you have "Let Window manager control created windows" or however it's worded in winecfg turned ON. That's normally the reason for the keyboard failing to respond.

---

### Post by JPMaximilian on 2007-01-11
If I do that, then DX won't run in full screen, it will run windowed and the keyboard will work.  I haven't been able to get it to run both full screen and with keyboard.

---

### Post by kullan&#305;c&#305; on 2007-01-11
> **JPMaximilian said:**
> If I do that, then DX won't run in full screen, it will run windowed and the keyboard will work.  I haven't been able to get it to run both full screen and with keyboard.
?
[www.unreadedpost.com(referers](www.unreadedpost.com(referers))

---

### Post by Enverex on 2007-01-11
What does "xrandr" in a terminal show? Sounds oddly like it's using xvidmode rather than xrandr to change screenmodes actually. Have you edited Wine's registry at any point?

---

### Post by JPMaximilian on 2007-01-11
I did change the output in mplayer at one point, certain movie files won't play by default, so I change it to xv, would this effect wine?

---

### Post by JPMaximilian on 2007-01-11
xrandr output:
```
 SZ:    Pixels          Physical       Refresh
*0   1280 x 800    ( 433mm x 271mm )  *60  
 1    640 x 350    ( 433mm x 271mm )   60  
 2    640 x 400    ( 433mm x 271mm )   60  
 3    720 x 400    ( 433mm x 271mm )   60  
 4    640 x 480    ( 433mm x 271mm )   60  
 5    800 x 600    ( 433mm x 271mm )   60  
 6   1024 x 768    ( 433mm x 271mm )   60  
 7    832 x 624    ( 433mm x 271mm )   60  
 8   1280 x 768    ( 433mm x 271mm )   60  
 9   1152 x 768    ( 433mm x 271mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none

```

---

### Post by Enverex on 2007-01-12
No, Wine uses its own "Windows like Registry" with the options contained within. I still think it sounds like an issue with your xorg.conf file.

---

