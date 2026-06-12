---
title: "Glest 2.0 installation"
date: 2006-04-16
forum: Gaming &amp; Leisure
---

### Post by zorkerz on 2006-04-16
Im haveing trouble installing glest 2.0.  I downloaded the data .deb and the glest .deb.  The data deb installes fine.  When i try to upack the other it says...

"sudo dpkg -i /home/zorkerz/Desktop/glest_1.0.10-7_i386.deb
Selecting previously deselected package glest.
(Reading database ... 115678 files and directories currently installed.)
Unpacking glest (from .../glest_1.0.10-7_i386.deb) ...
dpkg: dependency problems prevent configuration of glest:
 glest depends on libxerces26; however:
  Package libxerces26 is not installed.
 glest depends on libsmpeg0; however:
  Package libsmpeg0 is not installed.
dpkg: error processing glest (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 glest"

I checked both packages and i don't have them installed the version I do have installed has a c2 at the end of the name (so libxerces26cs and libsmpeg0c2).  Is there a way to get these two to work with glest or do I need to install the others somehow.
thanxs elias

---

### Post by zero0w on 2006-04-17
Try the Loki installer for Glest 2.0.0. It should work fine for Ubuntu Breezy as I am playing it now.

[http://www.glest.org/board/viewtopic.php?t=1204](http://www.glest.org/board/viewtopic.php?t=1204)

---

### Post by zorkerz on 2006-04-17
Thanx for this link.  I just downloaded the two files for the Loki installer but am unsure what to do with them.  One is an .md5 and the other .run.  By default they both try to open up in firefox but that deffinatly is not what i want.
thanx for the help
elias

---

### Post by Perfect Storm on 2006-04-17
```
sudo sh glest_2.0.0-multilanguage.run
```

---

### Post by Justbill on 2006-04-18
Hi Artificial Intelligence,

I am using "Dapper", I downloaded "glest_2.0.0-multilanguage.run" , the install seemed to go well,  su sh glest_2.0.0-multilanguage.run  , when I type "glest" I get this:

bill@Goliath:~$ glest
Exception: OpenGL extension not supported: GL_ARB_texture_env_crossbar, required for Glest

Any thoughts on what is causing this?

Thanks
Justbill

---

### Post by zero0w on 2006-04-18
It means your graphics card (or its driver) does not support the necessary OpenGL extension to render the 3D graphics required by the game.

Which display card are you using?

Also try this command and paste the output of console here to take a look:

$ glxinfo

---

### Post by Justbill on 2006-04-18
Here is that output:

glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
bill@Goliath:~$

I am currently using the onboard graphics on this machine, it is a 

Compaq Presario SR1426NX
2.93Ghz Pentium 4
1.5GB PC2-3200 DDR2 SDRAM
160GB 7200-RPM Serial ATA hard drive
dual booting win XP and "Dapper"

I am still fighting the GeForce FX 5200 install on this machine, hope to get it before long. tseliot has had some great suggestions on the nvidia threa, that I haven't had a chance to try yet.

So it sounds like I need to get that card working in order to play the game.

Thanks
Justbill

---

### Post by KingBahamut on 2006-04-18
Yes that would be the case.

---

