---
title: "wine very slow in 9.04"
date: 2009-04-26
forum: General Help
---

### Post by poo_22 on 2009-04-26
Im trying to run starcraft: brood war in wine, as i always did in 8.10, but its very laggy now (even though its a 10+ year old game and i have a new laptop)

using: 
Linux hpee 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

wine-1.1.20

is it because im on ext4?Should i downgrade??

HELP! i just want to play starcraft! lol

---

### Post by 3Miro on 2009-04-26
Did it work on wine 1.1.20 under 8.10 (might be a wine regression that you should report and they will fix it for the next version).

Do you have all the drivers installed properly?

Ext4 should make absolutely no difference or whatsoever.

I used to play SC:BW five years ago with wine, it should work fine.

---

### Post by poo_22 on 2009-04-26
Not sure how to check if i have all the right drivers, but compiz-fusion works (although my graphics card was blacklisted --> intel)

also how do i do a "wine regression"?

---

### Post by 3Miro on 2009-04-26
For regression: [http://wiki.winehq.org/RegressionTesting](http://wiki.winehq.org/RegressionTesting)

Do that if you have never tried it under wine 1.1.20 on 8.10. If it did run with 1.1.20 under 8.10, then the problem is different.

To check for drivers go to: System -> Admin -> Hardware Manager.

Another thing to try is to reinstall the game (did you upgrade to 9.04 or did you made a clean install?)

Check with winecfg (wine -> configure wine). Make sure you have selected a sound driver and take a look on the other settings. Check with winehq forum if there is a specific setting that needs to be set for the game to run.

---

### Post by lovinglinux on 2009-04-26
It runs slow for me too using wine 1.1.19 and 1.0.1, so I guess is not a regression problem.

Additionally, winecfg takes 3 minutes to load. Seriously!

I was able to install Steam and run the Portal demo like I did a few days ago on Hardy. They load pretty fast, but there was some performance drop, specially when passing through portals, which are essentially fps hungry.  In Hardy on the other hand, it played almost perfectly.

---

### Post by poo_22 on 2009-04-27
Ok i fixed it.. its the video drivers (duh!)

i followed this tutorial, and everything went fine. its straighforward, but use at your own risk!

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

