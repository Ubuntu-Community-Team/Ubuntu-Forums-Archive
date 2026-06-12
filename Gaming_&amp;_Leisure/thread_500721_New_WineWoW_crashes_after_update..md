---
title: "New Wine/WoW crashes after update."
date: 2007-07-14
forum: Gaming &amp; Leisure
---

### Post by Faust942 on 2007-07-14
I recently installed a new version of Wine and now my Warcraft is crashing.
I'll be able to login and be able to enter the world, but when my character model is loading it crashes.
Attached is the output from start to finish.

I don't know how to fix this. Please help.

---

### Post by DoktorSeven on 2007-07-14
Is it the 0.9.41 version of Wine released recently?  I had no trouble running WoW after the update myself.  I did notice references to direct3d in your output; have you tried using OpenGL rendering (see the WoW/Wine howto thread for details)?

---

### Post by Faust942 on 2007-07-14
Yes, shortly after I posted that I saw "d3d" also in the bug lines. So I restarted WoW and found out I had ApplyToForehead mod enabled. Disabled it, restarted WoW, same problem.

Would you like me to submit output again? This time with OpenGL?

Update:
I've tried everything. Removing my config.wtf file got me into the game and my character loaded, but when I set my Shaders and other settings it freezes. Why is this happening to the new Wine?! ARG! ....I feel like I should switch back to Windows just because of Wine and WoW.

---

### Post by Faust942 on 2007-07-14
When I add 
SET gxApi "opengl"
to my config.wtf file and restart WoW. It freezes half way into logging into a character. So my default config.wtf never had SET gxApi "opengl" in it....and it still ran better than d3d or adding SET gxApi "opengl".

Hopefully I didn't confuse...

---

### Post by DoktorSeven on 2007-07-14
Odd, I get no such problems.  Possibly some sort of config difference (I turn off a lot of effects and such since I'm using an old system), so maybe one of those is causing a problem.

---

### Post by Faust942 on 2007-07-14
Well Here is a my System Specs (Your gonna gasp at the video card):

Asrock 775i65GV Motherboard
(2) Western Digital 80GB 7200RPM Hard Drive
1GB DDR 400
64MB GeForce4 440 MX (Abit) [I don't have enough $$ to buy a new card atm.]

The stuff that doesn't matter:
(2) DVD-RW

I've been actually able to do alot of graphical stuff with this card. I got Beryl running on it at once. WoW was always a struggle to get working on Linux, but that's what I get for free software like Wine.

_Anyway, about my problem..._

I just don't know what to do. Graphics work when I set it too, 1024x768 but since I have a 19" monitor it looks stupid and choppy. When I set it to 1280x1024, it crashes. 

Remember, I've never used SET gxApi "opengl" in my config.wtf file. I've tried it but it gave horrible performance and froze when loading characters. I hate d3d for its textures (my mount turned pink! wtf).

---

### Post by Big_Rog on 2007-07-14
Could you add the output from the crashes when running in openGL as well?

the line:
```
err:d3d:state_multisampleaa Multisample antialiasing not supported by gl
```
suggests to me that you have an override for your video card settings (nVidia Settings program) that forces a higher AA level, or you haven't turned the antialiasing (AA) settings off in the video options inside WoW.  Come to think of it, I remember reading about WoW forcing 1xAA when one of the display settings was set to 0...

In addition to trying to run in openGL, have you added the registry tweak listed in the HowTo?

---

