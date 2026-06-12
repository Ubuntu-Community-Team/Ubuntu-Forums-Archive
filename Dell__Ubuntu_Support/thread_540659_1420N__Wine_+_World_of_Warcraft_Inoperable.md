---
title: "1420N:  Wine + World of Warcraft Inoperable"
date: 2007-09-01
forum: Dell  Ubuntu Support
---

### Post by Az7 on 2007-09-01
After installing the video drivers from Intel video drivers from gutsy and installing wine, I'm unable to get WoW playable.  The program will run by executing "wine /home/username/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -opengl", however the colors are way off and the game is not playable.  I'm attaching a screenshot for reference.  I've copied Config.WTF from a different computer that is successfully running WoW in wine, but I could post that or my xorg.conf if necessary.  Thanks.

---

### Post by angryfirelord on 2007-09-02
Try doing a couple different things:

-Are the colors different when you remove the opengl flag?
-Are the colors normal when you used Feisty?

---

### Post by Az7 on 2007-09-03
-Are the colors different when you remove the opengl flag?
  Yes, the colors are fine without opengl.  However, the characters do not render.  Everything else does, weapons, the ui, etc. 
-Are the colors normal when you used Feisty?
  Yes, everything is fine.  I can even play armagetron without any problems.

---

### Post by angryfirelord on 2007-09-03
Huh. It doesn't seem to be an OpenGL issue if other games are working fine. However, if you haven't tried it yet, use Feisty's intel drivers.

What version of wine are you using?

---

### Post by UbuntuniX on 2007-09-03
Have you tried to wine it outside of the wine desktop?

---

### Post by Az7 on 2007-09-03
Sorry, how do I wine it outside the wine desktop?

---

### Post by ramjet101 on 2007-11-24
I am having the same problem. Adding
  SET M2UseShaders "1"
to Config.wtf seems to help. If you still have corrupt UI icons after
this, then try:
  SET UIFaster "2"
I still have a problem with a corrupted minimap for which I haven't
found a workaround yet.

The above options only help the opengl mode, but don't have any
effect on d3d -- which actually looks fine out of the box, except for
the fact that the players don't render. :-/

---

### Post by onlinelli on 2008-01-03
Ramjet101,

I can confirm the problem and the workaround (for opengl). Did you find a way for d3d mode that the character renders?

---

