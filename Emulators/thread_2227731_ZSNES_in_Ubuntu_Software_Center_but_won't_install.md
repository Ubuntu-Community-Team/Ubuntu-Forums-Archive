---
title: "ZSNES in Ubuntu Software Center but won't install"
date: 2014-06-03
forum: Emulators
---

### Post by barbara6 on 2014-06-03
Hi everyone,  New Ubuntu user here. Ubuntu 14.04.  I've downloaded and installed NESTOPIA which works great! I love this little emulator. For my SNES gaming, however, I am unable to find a working emulator. ZSNES appears in the Software Center, but the install button is nowhere to be found. I get the message:  ```
There isn’t a software package called “zsnes” in your current software sources.
```  Higan doesn't work, probably because I am using a very underpowered laptop. (Acer V5-122P-0869/AMD A4-1250 APU with Radeon(TM) HD Graphics × 2/Gallium 0.4 on AMD KABINI). Higan's requirements are: Intel Core-series processor & OpenGL 3.2-capable graphics card.  Anyway, besides this minor issue, I'm really enjoying Ubuntu so far! The computer is overall much faster, except for wifi, than Windows 8.1.

SOLVED: sudo apt-get install zsnes

---

### Post by slickymaster on 2014-06-03
After selecting ZSNES, you'll find the install button in the far right. See the picture bellow:
[ATTACH=CONFIG]253707[/ATTACH]

---

### Post by barbara6 on 2014-06-03
Hi Slickymaster,

Mine does not display that button :(

It does for every other piece of software I downloaded (VLC, NESTOPIA, etc).

Here is a screenshot:

[ATTACH=CONFIG]253708[/ATTACH]

Just ran ```
sudo apt-get install zsnes
``` and seeing what that does...

---

### Post by barbara6 on 2014-06-03
That command in terminal worked. Solved!

---

### Post by slickymaster on 2014-06-03
Great you got it solved. Please don't forget to mark the thread as SOLVED using the Thread Tools menu item on the right of the toolbar.

---

