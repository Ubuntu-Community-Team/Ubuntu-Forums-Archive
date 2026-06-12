---
title: "Frets on Fire with 16-bit graphics"
date: 2008-03-16
forum: Gaming &amp; Leisure
---

### Post by Tea4all on 2008-03-16
I have been having problems running Frets on Fire. My graphics card only supports 16-bit. I have set this for other games just fine. How do I set this? Here is the output:```
(D) Initializing audio.
(D) Audio configuration: (44100, -16, 1)
(D) Initializing video.
(E) Couldn't find matching GLX visual
(E) Video setup failed. Make sure your graphics card supports 32 bit display modes.
Traceback (most recent call last):
  File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 68, in ?
  File "src/GameEngine.py", line 155, in __init__
  File "src/Video.py", line 61, in setMode
pygame.error: Couldn't find matching GLX visual

``` Also having problems with 3D chess if it helps.:confused:

---

### Post by Tea4all on 2008-03-16
*bump*

---

