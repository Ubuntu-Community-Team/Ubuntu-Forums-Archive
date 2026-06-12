---
title: "UT2004 running very slow"
date: 2007-02-24
forum: Gaming &amp; Leisure
---

### Post by SergeiFranco on 2007-02-24
Hello there, I have been searching for solution to my problem, and trying different things for almost a week, so I decided to make a post about it.
Here is the problem: UT2004 runs very slow on a decent setup.
My setup is:
1466Mhz Athlon XP (1700+)
512Mb Ram
160Gb HDD
GeForce FX6600GT 128MB AGP
KT400 VIA chipset 
I have tried with Ubuntu 6.10 (tried on both 386 and generic kernels), Kubuntu 6.10 clean install, then I compiled custom kernel (2.6.20). New kernel improved performance little bit. I have tried with drivers from repository and nvidia site (which was slightly faster aswell).
I have GART on, AGP is at 8x, DMA is on, direct rendering on.
I have tried on different video card - FX5200 (funny enough veryy similar performance).
In glxgears I get ~3300fps (which I believe is a bit low) on FX6600GT and ~1500fps on FX5200. Quake3 Arena runs beautifuly - Time demo at 1280x1024 with everything on high I get about 80fps.
In UT2004 in main menu I get about 30fps no matter what setting or resolution I use (tried 640x480 with everything on low and 1280x1024 everything on high), while in the game I get major slowdown in open area and long coridors (~10fps) the slow down is not affected by resolution or settings.
I remember when last time I ran UT2004 on Windows XP, it used to fly on Geforce4 card, 256MB of RAM and Duron CPU, I would assume that on FX6600GT it would be stupidly fast but clearly this is not the case...

---

### Post by Cappy on 2007-02-24
This probably won't help at all but I had a similar problem.
UT2004 lagged badly even if I turned every option to the minimum. It turns out that my gDesklets were causing it. Killing the gDesklets daemon gives me the same performance I get on Windows and since I'm a hardcore TAM player so I'm REALLY picky about my FPS.

---

### Post by ebichu on 2007-02-24
What drivers are you useing?
The ones from nvidia or the open source ones?

---

### Post by SergeiFranco on 2007-02-24
But I don't have gDesklets installed.
The issue happens with both drivers...
Oh I made a mistake it is 128Mb card.
But it should not matter I googled reviews of that video card and it was getting pretty good results in UT2K4....

---

### Post by ebichu on 2007-02-24
Yea, i got somewhat nice fps with my radeon9200 se. i think you are using mesa drivers instead of binary.

---

### Post by SergeiFranco on 2007-02-24
I am defenitely not using mesa driver (I am using NVIDIA*.run package from nvidia site)...

---

### Post by hikaricore on 2007-02-24
Please check these from terminal:

```
glxinfo | grep rendering
```

^  This should return - *direct rendering: yes*

also run:

```
top
```

Check the top few rows under the white column bar where it says: %cpu and %mem, to make sure that nothing is using an insane amount of cpu or memory.  If anything there is using over 30-50% cpu or memory, this is probably the issue.  Let us know if you see any processes that are overusing memory/cpu their name with be on the right hand side directly across from the percentages.

---

### Post by SergeiFranco on 2007-02-25
I have direct rendering on (grep returns yes)
Also my cpu usage is about 1% and memory usage about 75% full (no swap usage, swap on at 1.44Gb).

---

