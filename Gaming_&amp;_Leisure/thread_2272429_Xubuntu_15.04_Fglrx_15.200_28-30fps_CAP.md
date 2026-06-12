---
title: "Xubuntu 15.04 Fglrx 15.200 28-30fps CAP"
date: 2015-04-06
forum: Gaming &amp; Leisure
---

### Post by james_riddick on 2015-04-06
I'm just posting this here to see if anyone else has experienced a problem with these beta drivers capping fps to a very low limit no matter how low of graphics settings you use.

The two games I have been using to test are: Warthunder & Pillars of Eternity, both appear to not exceed 28 or 30fps. I have a R9 290x and have tried 1080p and 4k resoluation(my native). In Ubuntu 14.10 with Omega 14.10 drivers I was getting upto 60fps if not more (depending on scene) and I never dipped below 30fps thats for sure.

Does anyone know of any issues that might exist to cause this? am I by myself with this problem? 

I have checked to ensure I have AMD drivers installed and NOT opensource. Even so, opensource drivers should be better then this. 

Totally Stumped :(


PS. I should mention that desktop seems a bit choppy also. My monitor is set to 60hz and even shows up as 60hz (this was the first thing I checked).

---

### Post by james_riddick on 2015-04-07
I believe I mostly fixed my problem. After several reinstalls (and failures) of Fglrx, along with removal of xorg conf files, and also installing steam before driver install and removing its impostor files (code below) THEN installing driver on top.

I used this code to remove the steam files that may have been contributing to the issue.
find ~/.steam/root/ \( -name "libgcc_s.so*" -o -name "libstdc++.so*" -o -name "libxcb.so*" \) -print -delete


Still get poor performance in War Thunder but its allot better, even desktop runs better. I can't be sure that what I did fixed the issue or it was just some magic fairy dust along the way...

---

### Post by jamesjogi08 on 2015-04-11
[COLOR=#000000]with removal of xorg conf files, and also installing steam before driver install and removing its impostor files ...!!!





____________________________________________________________________
[/COLOR][TABLE="width: 127"]
[TR]
  [TD="width: 127"]Our excellent online  [learnalanguage  - learn german](http://www.learnalanguage.com/learn-german/) training programs lead you to [learn  portuguese](http://www.learnalanguage.com/learn-portuguese/) success in the We also offer latest  and [E-spanyol](http://www.e-spanyol.hu/en/) with 100% success [Internet  polyglot](http://www.internetpolyglot.com/)[/TD]
[/TR]
[/TABLE]

---

