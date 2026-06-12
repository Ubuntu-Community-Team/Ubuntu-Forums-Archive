---
title: "Low FPS in Counter Strike Source"
date: 2007-03-02
forum: Gaming &amp; Leisure
---

### Post by janz84 on 2007-03-02
Is it just me or does the FPS always suck when running stuff in wine?

I installed steam into wine and copied my counter strike source folder along with the gcfs on the wine setup. 

So with wine and CSS I get 10-20fps and with windoze and css i get 60-120fps...

any suggestions?

---

### Post by Sqwishy on 2007-03-02
That's because Source and Windows uses direct x, the other operating systems (like linux) use opengl, and wine converts the dx calls to opengl calls, so its slower! If you have a game that uses opengl it's faster, like games that were ported to macs like jedi academy will usualy run goodly on wine.

---

### Post by bastiegast on 2007-03-02
> **Sqwishy said:**
> That's because Source and Windows uses direct x, the other operating systems (like linux) use opengl, and wine converts the dx calls to opengl calls, so its slower! If you have a game that uses opengl it's faster, like games that were ported to macs like jedi academy will usualy run goodly on wine.

But it won't cause a 80 % performance hit. CSS is/should be playable under linux with little or no performance loss. However lately I have experienced some problems too, you might want to downgrade to wine 0.9.29. I'm currently seeing what 0.9.32 (just released) can do.

---

### Post by janz84 on 2007-03-02
hmmm... would it be because I using wine 0.9.30 amd64?

---

### Post by Techman010 on 2007-03-03
yeah, I am having the same problem.
The test in CSS in windows gives me 147 FPS,
The test in CSS in ubuntu gives me 102 FPS,
It doesn't sound bad but during the game my fps has gone down lower than 30 FPS and there is some frame skips every now and then.  In windows, my FPS never goes below 100 FPS.
i'm using the PC version of ubuntu 6.10.

HL2 is much worse in FPS from windows to ubuntu, which I would assume because of the bigger environments.

BTW: I'm running a Core 2 Duo 6600, 7900 GT, 2 GB of RAM

---

### Post by YokoZar on 2007-03-03
You're not using an ATI card by any chance, are you?

What drivers are you using?

---

### Post by conjur3r on 2007-03-03
Have you told CSS to use opengl rather than directx?

Edit: I had another look and there is no OpenGL option.  Maybe this only existing in the older CS rather than CSS

---

### Post by Techman010 on 2007-03-04
YokoZar: I'm using a Nvidia 7900 GT.


BTW: i'm not complaining, I just posted because I was just wondering if this could be fixed by newer versions of wine or if I was doing something wrong.

---

