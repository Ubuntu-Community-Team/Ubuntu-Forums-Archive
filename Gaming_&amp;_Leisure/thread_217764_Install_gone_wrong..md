---
title: "Install gone wrong."
date: 2006-07-17
forum: Gaming &amp; Leisure
---

### Post by sdmike on 2006-07-17
I installed tremulous and after the install GUI it went back to the terminal and gave me this error:


[COLOR="Red"]***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem[/COLOR]

So what should I do to fix this?

---

### Post by gerbman on 2006-07-17
You don't have accelerated graphics enabled. You'll need to install the drivers if you have a dedicated video card. You might be out of luck if you don't have a video card.

---

### Post by sdmike on 2006-07-17
Then I think I'm out of luck because I'm using my laptop which has an ATI radeon xpress 200m with 128mb. So then there's nothing I can do?

---

### Post by gerbman on 2006-07-17
> **sdmike said:**
> Then I think I'm out of luck because I'm using my laptop which has an ATI radeon xpress 200m with 128mb. So then there's nothing I can do?I think you should be able to use [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") how-to. It is supposed to support the x-series cards.

---

