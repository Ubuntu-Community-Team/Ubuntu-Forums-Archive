---
title: "TitaniumGL 3D drivers (linux version)"
date: 2012-03-07
forum: Gaming &amp; Leisure
---

### Post by Geri_lgfx on 2012-03-07
[B]Linux version of TitaniumGL is now finally released!

[IMG]http://legend.uw.hu/TitaniumGL/img/tglogo.jpg[/IMG]

[/B] TitaniumGL is a **FREEWARE** driver architecture. Project's goal is to support OpenGL on graphics cards with broken/bad or missing OpenGL drivers. 
[SIZE=1]( WARNING: The author does not possess an OpenGL license  from SGI, and makes no claim that TitaniumGL is in any way a compatible  replacement for OpenGL or associated with SGI. USE AT YOUR OWN RISK. ) [/SIZE]

*************************
WHAT IS THIS, I DO NOT EVEN...
*************************
TitaniumGL driver meant for computers where no opengl drivers available  for the system. Its compatible with a several platforms, and now, since  cthulhu does not coming out from the computer when using the linux  version, i released it publically.

*************
HOW IT WORKS?
*************
Just like any other opengl implementation for linux, this is also a  libGL.so.1, that you should copy to your system directory (read the  readme for more informations). No other actions required to install it. 

TitaniumGL renders the scene with all of your (well, up to 4 max) cpu cores in your computer. **It can run almost ALL popular opensource game PLAYABLE (over 24 fps) with a core2duo cpu in enjoyable screen resolutions.**

Warning: TitaniumGL is **NOT **meant to run CAD applications, built-in legacy/useless gear renderer tools (!!!!!!!!), its **ONLY **meant to run **REAL** games! (however, maybee other kind of softwares also run. there is a compatibility list on the webpage available)

*there is only 32-bit version at the moment, 64 bit version is not yet available. HOWEVER, you can use the 32-bit version on 64-bit systems, to run 32-bit games*

Why it wasnt released earlyer?
***********************
There was a lot of bugs and almost unfixable compatibility issues,  becouse the linux graphics api and the x11's documentation is simply  useless, and the quality of linux rendering infrastructures simply makes  no sense. Also my code had a few bugs that only caused mess on the  Linux platform. But now, they are not any more exist, so its a good time  to release the software. 

Limitations:
********
-The software under linux is somewhat slower than the Windows version, due to linux kernel's thread handling.
-In some systems/cases, for some strange reason, only one cpu core being used.
-On some systems, rendering speed capped to VSYNC.
-On some systems, rendering speed capped to 70, or 40 fps, or some strange speed like that

i wish you all happy using.
download & read more informations on the webpage and in the readme file.

**download: [http://TitaniumGL.tk]("http://titaniumgl.tk/")**

---

