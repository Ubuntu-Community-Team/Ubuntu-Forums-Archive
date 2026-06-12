---
title: "Dual Monitors on Dell 600m Feisty"
date: 2007-10-11
forum: Dell  Ubuntu Support
---

### Post by Scothiam on 2007-10-11
I've read a few posts regarding this and still no real answer on how to get this going...

I've tried a few tutorials and have basically found that my Radeon Mobility 9000 is too old for the latest driver,  yet I cannot seem to use the old driver, 8.28.8, on Ubuntu Feisty.

Do I need to downgrade to an older version of Ubuntu?

I'm afraid my new ubuntu install is now just as messy as my old XP after all these failed attempts at installing drivers...

Cheers,

UPDATE: I've updated to 7.10 and although the "Screens and Graphics" admin menu/area is great (sees my second monitor), still no luck extending the desktop (or even using the second monitor as anything other than a 640x480 clone of my 1024x786 screen...)
Recommend I switch to 6.06 LTS?

---

### Post by Scothiam on 2007-11-22
OKAY, got I went back to 6.06 and used the instructions here [http://ubuntufan.wordpress.com/2007/04/04/dual-display-on-dell-latitude-d600/](http://ubuntufan.wordpress.com/2007/04/04/dual-display-on-dell-latitude-d600/) and eventually got dual displays up and running by editing the xorg.conf file (a lot).
I was able to keep this config working after upgrading to 6.10, and then 7.04, however, this config no longer worked in 7.10 (I do not recommend updating from 7.04 to 7.10 with this config, do a clean install)

I was able to get dual displays working in 7.10 by following the instructions here [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2), though video playback in no broken see my new thread here [http://ubuntuforums.org/showthread.php?t=620249](http://ubuntuforums.org/showthread.php?t=620249)

---

