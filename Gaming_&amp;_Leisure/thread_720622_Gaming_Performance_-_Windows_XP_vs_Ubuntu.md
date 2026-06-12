---
title: "Gaming Performance - Windows XP vs Ubuntu"
date: 2008-03-10
forum: Gaming &amp; Leisure
---

### Post by HanDy_man on 2008-03-10
I have run same demo of Quake 3 under Ubuntu and Windowz XP. Maximal frame rate in XP is 120FPS, Ubuntu - 90FPS (native version of Quake 3). I`m using real time kernel + optimizations for my CPU and dedicated X sesion and no compiz. My question is what cause that difference? May be my case is isolated. Can DMA affect performance?

my spec is:

Celeron 1.72 Willamette
2x128 SDRAM 133MHZ
GF 2 MX400 64MB 200/333
Seagate 120GB ATA (500MB swap)

---

### Post by Ardrias on 2008-03-10
Drivers for the video card, most likely.

---

### Post by HanDy_man on 2008-03-10
AMD/ATi cards have open source drivers so if I buy new PC with AMD/ATi card there will be no such problem?

---

### Post by acoustibop on 2008-03-10
If you want optimum performance, you'll need the proprietary fglrx driver for an ATI card rather than the open source ones, HanDy_man.  That means you'll need a Radeon 9550 or better, as the fglrx driver doesn't support cards below the 9550.

---

### Post by doorknob60 on 2008-03-10
Unless something's changed really recently, you want an nVidia card for sure if you're getting a new one. THe reason the difference is probably because you have an old card and the driver isn't as good for the older cards maybe? Just a guess.

---

### Post by acoustibop on 2008-03-10
Actually, things have changed a bit recently, doorknob60 - AMD are now taking a much more proactive stance towards Linux and the drivers are much improved and improving.  They're still not where they should be, I think - but getting there.

---

### Post by forrestcupp on 2008-03-10
> **HanDy_man said:**
> AMD/ATi cards have open source drivers so if I buy new PC with AMD/ATi card there will be no such problem?

Wrong.  The open source drivers don't currently support newer ATI cards very well.  If you get an HD series card, it's likely to be a long time before you see good open source drivers for that, seeing how they released their specs for everything *but* the HD series.

---

### Post by Vadi on 2008-03-10
I went with nVidia myself, and have been quite happy.

---

### Post by karth on 2008-03-11
Actually, having q3 maxing at 90fps is not because of the video card, but because of the game itself. There's a console command that lets you unlock the maxfps

This will max at 150
```
sv_maxfps 150
```

This will be unlimited
```
sv_maxfps 0
```

I suggest you try setting this variable before buying anything.

---

### Post by acoustibop on 2008-03-11
> **forrestcupp said:**
> Wrong.  The open source drivers don't currently support newer ATI cards very well.  If you get an HD series card, it's likely to be a long time before you see good open source drivers for that, seeing how they released their specs for everything *but* the HD series.

Yes, but who's going to get an ATI HD card and then run it with the open source drivers, forrestcupp?  The fglrx driver should work fine with them, and give far better performance than with the open source drivers.

---

### Post by Sammi on 2008-03-11
Even the official proprietary drivers from Nvidia, which are supposed to be the best graphics card drivers for Linux, do not perform as well as their Windows counter parts.

Has nothing to do with the performance of "Linux" itself, but rather the lacking Linux support from graphics card vendors.

---

### Post by desertboy on 2008-03-12
Really, Nvidia's beta drivers seem a little faster to me than windows (Vista) on Alien Arena 2008 and C&C (In wine which is not really a fair comparison)) I think Nvidia's biggest downfall is not putting new version in the repo's often enough so you hae to go through a ball ache installing beta drivers where as windows users need only double click and exe and click next a few times and then reboot.Also Kernel updates break your beta drivers and you have to reinstall them.

---

