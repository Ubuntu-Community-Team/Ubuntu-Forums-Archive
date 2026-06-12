---
title: "Emerald SLOW in Gutsy."
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by jimmy the saint on 2007-10-24
Everything works pretty well in Gutsy so I figured I would make it look good too.  I installed Emerald theme manager and my system suddenly went from good to slow.  The animations are choppy and often lag.  Firefox seems to be especially bad.  Sometimes just changing tabs takes a two to four seconds.  To my thinking, Emerald itself should not cause this kind of slowdown.  Any ideas?

---

### Post by jimmy the saint on 2007-10-24
Nobody else has this problem?  Could it be an issue with Nvidia perhaps?

---

### Post by thespankguy on 2007-10-24
gutsy as a whole has been somewhat slower than xp for me, but since i installed emerald i've seen no difference.

---

### Post by gerryk on 2007-10-25
I've seen the same issue, using both the intel server and the i810 server. My initial dist-upgrade displayed this issue, so I built a fresh install which performed well until I installed emerald and libemeraldengine0. I then installed a few themes and initially all seemed well. However, Firefox caused xorg to crash and OO.o caused the choppy animation described above.
Xorg.log has no dump reports.

Uninstalling emerald and libemeraldengine0 and restarting X restores the system to a useable state.

---

### Post by sinaen on 2007-10-25
my sistem is like running trgoug sand or syrup its slow especially firefox. it doesnt starts to write this as yet.
now the ficrst letters popped up. so you understand to wrcite long messages is really hard for me right now.
:(
this mesage took about 10-15 minutes to be completed.

---

### Post by sinaen on 2007-10-25
A Deinstallation of the said packages brougt before a restart of the ex-system a ntremendous fastness to the windows but not yet the text :D whoho thacnks....

---

### Post by KTrigger on 2007-11-01
I haven't experienced any slowdowns while using emerald, however I have had it crash on me from time to time (title bar and borders disappear,)  I haven't really looked into the logs for an error message as I usually just restart it with no problems.  The crashes usually occur when I'm alt-tabbing with previews or moving windows around on the expo view.

---

### Post by Zorael on 2007-11-01
As for the crashing, see [http://ubuntuforums.org/showthread.php?t=599539](http://ubuntuforums.org/showthread.php?t=599539) for a dirty workaround.

As for the slow Emerald, did you upgrade from Feisty? Maybe you need to apt-get **purge** emerald and its library, not sure - upgrades who are experiencing weird showstopper issues with Compiz can generally fix it by purging. Remnants of Compiz/Emerald/Beryl from Treviños repository don't play well with Gutsy's versions.

```
$ sudo apt-get purge compiz* libcompiz* emerald* libemerald*
```

---

### Post by gerryk on 2007-11-02
I had the issue in both an upgrade and a fresh install from gutsy only repos.

---

### Post by ryanlindstedt on 2007-12-12
i have this exact same problem as well. fresh 64bit gutsy install, compiz, then emerald and wham the problem is there. I have tried a couple of times as well.

---

### Post by bcn17 on 2007-12-30
I just installed:
sudo aptitude install emerald libemeraldengine0
My system was very slow. I especially noticed when changing tabs. 
sudo aptitude purge emerald libemeraldengive0 and restart complete fix. 
Any ideas as to what causes this?
Gutsy/64 nvidia accelerated graphics driver on a nvidia 8600M GT - compiz is already installed. haven't tried it without compiz already installed.

---

### Post by spandanj on 2008-03-10
I have this same problem right now.

emerald worked fine for about 2 months since i installed gutsy in jan 2008. then, one day it just became really slow....to the point of unusable. so i had to uninstall. i reinstalled a couple times. everytime it would make ubuntu very very very slow...

no solution yet.

---

### Post by spandanj on 2008-03-10
for someone who's trying to solve this problem (IS THERE?)

it becomes slow only AFTER i try to resize a window. up until that point, ubuntu is running fast and ok. after a window resize, everything becomes slow.

---

### Post by flowevd on 2008-03-10
hi 

i have the same problem.

apparently, if you're using an nvidia card it might be a bug with the combination emerald+compiz+nvidia

see here:
 
[http://forum.compiz-fusion.org/showthread.php?t=5089](http://forum.compiz-fusion.org/showthread.php?t=5089)

--
flowevd

---

### Post by CarnivorouZ on 2008-03-11
It's not just slow on the Nvidia cards.  I have an ATI Radeon and my animations work, but they are often laggy.  I just didn't know that it was likely Emerald that was causing this until this thread.

---

### Post by spandanj on 2008-03-13
SOLVED

Here's what i did:

i made a new user--Guest. logged into guest. since i had emerald installed, it worked fine in guest. i could even resize a window without slowing it down. so then i realized that the problem must lie in my own account not in the general emerald installation. so, i went back to my account. i opened up ".emerald" in my home folder. there were 2 folders--theme and themes. and, a config file. i deleted all three. restarted emerald theme manager, and added a new theme. now, everything works fine.:):p:-D8)\\:D/:-P;-)=D>

---

### Post by m3alnemer on 2008-05-14
> **spandanj said:**
> SOLVED

Here's what i did:

i made a new user--Guest. logged into guest. since i had emerald installed, it worked fine in guest. i could even resize a window without slowing it down. so then i realized that the problem must lie in my own account not in the general emerald installation. so, i went back to my account. i opened up ".emerald" in my home folder. there were 2 folders--theme and themes. and, a config file. i deleted all three. restarted emerald theme manager, and added a new theme. now, everything works fine.:):p:-D8)\\:D/:-P;-)=D>

Worked!
Thanks!

---

