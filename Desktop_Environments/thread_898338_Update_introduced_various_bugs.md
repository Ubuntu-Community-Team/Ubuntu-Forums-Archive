---
title: "Update introduced various bugs"
date: 2008-08-23
forum: Desktop Environments
---

### Post by delude on 2008-08-23
I updated some packages suggested by the update manager yesterday (it was a long list, i don't know where it is logged so I can post it).
After I rebooted the desktop looked weird. The theme was all messed up (i had the default one before) - now the icons are from clearlooks i believe, the windows have no buttons, chosing themes from the Appearence application doesn't do anything, re-installing themes either. I don't use desktop effects or anything like that - just the default theme. A thread describing a similar problem, with no solution yet is here: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5531136](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5531136)
I decided to start a new one because my problem doesn't end here.

My screen resolution was also changed to a higher than my video card supports (appears viewable but outside screen borders). The screen resolution application doesn't do anything either, I haven't played with xorg.conf to try to fix it yet. 

Some gnome applets started behaving strangly - for instance the System Monitor applet had a very different configuration - everything was black, very short refresh time, and different monitor tabs were active.

The Shut down button logs off the user instead right away instead of letting me choose what action to take. Something I saw described as a caveat of Intrepid alpha 4. 

Any ideas what could cause all those problems?

---

### Post by cdiggity on 2008-08-26
I have the same problem.
Yesterday I got logged off when I am pretty sure I hit suspend.  Later on a resume from suspend failed and I had to cycle the power.

When the computer booted this morning my icons are all different and I can't find the same ones again.

Any ideas on how to fix or has a launchpad bug been filed?

---

### Post by cdiggity on 2008-09-22
followed instructions for suspend/resume on thinkwiki for hardy and it is working now.  old gutsy settings were causing problems

---

