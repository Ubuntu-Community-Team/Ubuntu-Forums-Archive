---
title: "Video Card Problems UT2004"
date: 2006-12-12
forum: Gaming &amp; Leisure
---

### Post by koolguynet on 2006-12-12
Hello all,
I am running Edgy and just installed UT2004 (using the linux installer).  The program installed wonderfully, but the video sucked so I went back and installed the proprietary drivers for my card, ATI Mobility Radeon 9000.  That seemed to go smooth, and the video on the game looked great.  The menu looks great, but everytime I go to launch a game it hangs and crashes KDE.  I changed the setting on the game to software rendering and the problem goes away, but with OpenGL it just dies.  This leads me to believe it has something to do with how my video card is set up.  Help!  (Let me know whatever information would be useful)

---

### Post by koolguynet on 2006-12-12
Any takers on helping me out?  :p

---

### Post by Tuna-Fish on 2006-12-13
what does typing fglrxinfo in the terminal print?

---

### Post by Tuna-Fish on 2006-12-13
Just to point out, the proprietary drivers for ati cards (fglrx) is notorious for being very hard to install properly.

Instructions here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

fglrxinfo is used to determine what drivers you are using at the moment, my output for it is:

```

tuna@tunamasiina:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```
If it prints anything at all about "mesa", then you aren't actually using fglrx.

---

### Post by koolguynet on 2006-12-13
Here it is.  Thanks for taking a look at it.

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

---

### Post by Tuna-Fish on 2006-12-13
Seems to be ok. Sounds weird. Does other 3d work properly? glxgears for example.

---

### Post by koolguynet on 2006-12-13
glxgears -printfps
5057 frames in 5.0 seconds = 1011.315 FPS
5007 frames in 5.0 seconds = 1001.359 FPS
4957 frames in 5.0 seconds = 991.387 FPS
5063 frames in 5.0 seconds = 1012.569 FPS

---

