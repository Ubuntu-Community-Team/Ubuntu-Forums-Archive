---
title: "wine, CSS and graphic drivers"
date: 2007-07-25
forum: Gaming &amp; Leisure
---

### Post by Arizon_Dread on 2007-07-25
alright. I did search but i didn't find anyone with the same problem.

I've got:
motherboard: msi K8MM3-V
processor: AMD sempron 3000+
graphic card: GeForce FX 5200 128 mb
and wine-0.9.41

winecfg is set to run in windows vista mode.
158 
when i launch the game, i get a message saying that my graphical drivers are out of date (even though I just updated my computer) and that I'm using windows xp although i set winecfg to windowsvista mode. I am able to choose "play anyway" or something similar. the game works, but the graphic seems funny somehow.. it's like playing with 640 x 480 even though I've chosen 1024 x 768 or 1280 x 1024. and it's no 3D-feel. and it's also lagging way to much to be playable. 

it seems to me that my fake windows cant find my linux graphical drives, but i might be terribly wrong.

any suggenstions?

---

### Post by w116tjb on 2007-07-25
Have you enabled the restricted repository and updated the drivers that way?

---

### Post by Arizon_Dread on 2007-07-25
I don't know how.. I'm a bit of a n00b, you see..:shock:

---

### Post by frodon on 2007-07-26
> **Arizon_Dread said:**
> winecfg is set to run in windows vista mode.Really bad idea IMO.

To run CS:S with best stability and performances you should use the XP mode or even the win98 mode, the win98 mode is the more stable.

Be sure to read this :
[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)

And check that in winecfg, in the display tab you have set "vertex shader" to material.

---

### Post by Arizon_Dread on 2007-07-26
ok. I've tried windows NT, windows XP and windows Vista and it all gives the same problem. 
when I start CSS i get that dialogue saying that I have to update my drives. it says that I'm running Windows XP no matter what I set in wineCFG.

do you think the drives will work if i try with -98?

will try it out tonight when I get home from work.

---

