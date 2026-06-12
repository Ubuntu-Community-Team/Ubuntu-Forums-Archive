---
title: "Valve Portal Revisit: DirectDraw"
date: 2007-11-24
forum: Gaming &amp; Leisure
---

### Post by Kat of Zion on 2007-11-24
So I bought portal and found that while everything checks out graphic wise (glx gears works fantastic, direct3D works fantastic) Direct Draw does not function properly.  While it is present and all the tests check out, the cube crawls (vs. bouncing).  It moves really........really......slow.  It resembles the same issue I was having specific to playing Portal where any motion in the game would take donkey years to perform.

Before buying the game, I checked out to see if my [video card]("http://http://www.amd.com/us-en/Processors/ProductInformation/0,,30_118_14603_14628%5E14631,00.html") would face compatibility issues.  Given that other players have gotten portal to work and that it indeed fits the requirements (except for running Vista...yuck!), I dont really think it is my video card.

Oh, and Im using Crossover Office to run Portal (vs. Wine or Cedega -- the game did not work at all in any of these programs).

Kat

---

### Post by UltimaDude on 2007-11-24
Have you installed your drivers?

---

### Post by Kat of Zion on 2007-11-24
Well I have gotten games working in the past so I assume I have drivers for it.  However is there a possibility of an updated driver for my vid card that I might be overlooking?

---

### Post by bastiegast on 2007-11-24
Tell us what video card you use, if it is an ati card it might be a driver issue although recently their drivers improved drastically. These improved drivers are not standard in Ubuntu however. Also you say you tried the directdraw tests. From that I take you installed directx 9.0 from that guide of wine-review. You don't need to do that. actually it might be the cause of the slowness. Wine has its own directx implementation and installing directx is not required for portal.

My advice: If you have a nvidia card: Start over with a fresh .wine directory(remove /home/username/.wine CAUTION: this will remove all programs you've installed in wine and you will need to reinstall them), if you have an ati card: try to install the 9.42 or 9.41 drivers. search the forums for instructions. After that statr over with a fresh .wine directory...

---

### Post by Kat of Zion on 2007-11-24
If you read from above, I did link to the specs of my card.  It is an ATI card.

I will look into the direct x problem, however our problem started before we installed direct X

Kat

---

### Post by bastiegast on 2007-11-24
> **Kat of Zion said:**
> If you read from above, I did link to the specs of my card.  It is an ATI card.

I will look into the direct x problem, however our problem started before we installed direct X

Kat

Then you should probably look at your driver version. If you never touched the driver you installed from the ubuntu repositories then you should upgrade it to 9.42. 
btw. Your link is broken, remove the [www.http.com//](www.http.com//)

---

