---
title: "What Video Card are you having success with Ubuntu 10.04?"
date: 2011-01-27
forum: Gaming &amp; Leisure
---

### Post by SVEN1 on 2011-01-27
Overall impressions of your cards performance?

---

### Post by realzippy on 2011-01-27
Well,what *exactly* is success??

To me it means:

16x AntiAliased,8x Anisotropicfiltered,SyncedtoVrefresh Desktop
with 5 Mb Compiz Skydome animated backround,everything snappy no matter
if flash,DVD,game and work stuff running synchroniously.
This works since Ubuntu 6.10 flawlessly with NVIDIA cards/drivers.
(GT 7950,GTX 9800,GTX 260)..
Overall impressions ??
Would say: perfectly.

---

### Post by Sylos on 2011-01-27
NVIDIA Geforce FX5500 PCI card!

Yeah....thats right....I said PCI.

Bought it for a rig rebuild that went south and now it sits in my second PC replacing the AGP Radeon 9200 that has no driver support (cheers for that AMD).

The card performs its function well. I get the res I want and I get to clone it to my TV via S-video. And when I finally get a decent TV I will use the second VGA that the card has.

It aint exciting or flash....but it is a success for me.

---

### Post by mips on 2011-01-27
Anything nVidia is a sure thing, the later the greater. 
Got a XFX 9600GT

---

### Post by rizzeh on 2011-01-29
I have a GeForce 250 GTS on the desktop and GeForce Go 6400 on laptop. Both work well. Before i had two GeForce 8600GT in SLI mode also working well.

had to tweak laptop drivers to reduce core clock speed - saves batteries. Laptop's video xorg section: 
```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option  "RegistryDwords"    "PowerMizerEnable=0x1; PerfLevelSrc=0x2233; PowerMizerDefault=0x3"
    #level 0×1 = highest
    #level 0×3 = lowest
EndSection
 
```

---

### Post by Perfect Storm on 2011-01-29
4800 GTX 128MB (past)
6600 GT 256MB (past)
6800 GTX 512MB (past)
8800 GTX 756MB (past)
GTX 285  1000MB (current)

Never had any trouble with those cards, and they worked perfectly.

---

### Post by handy on 2011-01-29
Just to be different:

AMD/ATi HD2600Pro 256MB, which has been running on the current dev' packages & kernels that make up the driver stack, for over 15 months now.

For most of that time it has been satisfactory, for roughly the last 6 months it has been amazing. 2D is brilliant, movies no tearing (1920x1200), the 3D is still not capable of playing very complex 3D games.

Gallium is coming along fast, the dev's have started work on optimisation, so the time is fast approaching (at last) where gaining speed is becoming the top priority. :)

Box_2: Has an nVidia AGP 7950GT 512MB by XFX. It works fine with the closed drivers, I wouldn't attempt to run it using the open ones.

Past cards:

6600GT AGP
6800GT AGP

---

### Post by alexandrius on 2011-01-30
Geforce 9500GT 512mb, works great :) (current)
Geforce MX4500 also works great, with old drivers (old)

---

### Post by Refresh100 on 2011-01-30
Well... I'm using my built in ATI Radeon HD3200 Graphics Card in my laptop and that can sure get some gaming done. There are, however, some lag issues but I think that's just more of me have have 20 programs open at the same time. ;)

---

### Post by GWBouge on 2011-01-30
GeForce 8800GTS 512MB (last)
GeForce GTX 460 768MB (current)

Both work great with oodles of Compiz effects.  The 8800 kept up well at near-max quality on most 3d games I've tried (Prey, Doom 3, Nexuiz, Savage 2, etc).  With the 460, I can play maxed out at a reasonable frame rate.

---

