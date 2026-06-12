---
title: "twinview problems"
date: 2006-08-21
forum: Desktop Environments
---

### Post by patsissons on 2006-08-21
I had been running X for about 12 days or so and finally had to restart, upon restarting my x was completely borked.  I took a look at the xorg.conf file only to find that it had been mangled into a mix of half new half old config lines.  Definitely bizarre.  fortunately, I keep a backup of a working copy of my xorg.conf file.  So I restored the file, restarted X, (I was also forced to delete some kde screen config file as well), and watched the results.  Turns out that I managed to fix most of the problems, but now the twinview is not being properly recognized by KDE.  earlier, KDE would split my large twinview desktop into two virtual desktops (seperate backgrounds, maximizing windows to a specific desktop, etc...).  Now KDE just treats my desktop as one large desktop, this is extremely annoying.  Any ideas on why this happened all of a sudden, and more importantly, how to fix it.  It's driving me crazy! ](*,)

---

### Post by patsissons on 2006-08-21
After some stress testing (pun aggressively intended), I managed to narrow the problem down inside the xorg.conf file.  Clearly there have been some driver changes, maybe even KDE display changes but that I cannot confirm...  The new drivers DO NOT allow you to have a non-square profile in twinview mode.  i.e. you must have both monitors set at the same resolution, otherwise only one monitor will turn on (at least in my case).  Futhermore, if you have the option NoTwinViewXineramaInfo set then you will get a giant desktop, this was not the case before, in fact i think the earlier drivers disregarded this option as i do not remember it doing anything.  Finally, the displayconfig module in KDE cannot enumerate your display vertical refresh frequencies (probably because it is confused with your large desktop).  Because of this, the display module will not work at all.  Fortunately there isn't much you can do in the module anyways, so there is no real loss.

That's all I managed to figure out tonight, any other feedback will be warmly welcomed.

---

