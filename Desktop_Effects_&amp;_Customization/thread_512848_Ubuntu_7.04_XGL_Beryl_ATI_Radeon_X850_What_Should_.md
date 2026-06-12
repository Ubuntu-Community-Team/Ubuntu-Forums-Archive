---
title: "Ubuntu 7.04 XGL Beryl ATI Radeon X850 What Should I Do?"
date: 2007-07-29
forum: Desktop Effects &amp; Customization
---

### Post by vxd_error on 2007-07-29
Hello to all, i have read tons of threads and articles published over the last few months trying to peg this one but I seem to be getting conflicting and/or inaccurate information.  I am running a fresh install of Ubuntu 7.04 with all the updates.  I have an ATI Radeon XT850X and my goal is to run XGL and Beryl.  I am very familiar with the packages / xorg.conf and linux.  The problem i am running into is which ATI driver I should be using?  I have tried xorg-driver-fglrx package and have also tried the ati proprietary packaged drivers (from the ATI site).  Ive tried xorg.conf video drivers 'ati' 'radeon' 'fglrx' in various combinations with Composite on and off.  Ive also tried using the 'envy' script (incase im missing some xorg.conf parameters) but I just cant seem to get it to work properly.  If i use the ati proprietary drivers and run xgl, it executes but the graphics are all scrambled.  If i run the xorg-driver-fglrx driver it seems like it works with beryl but the performance is horrible and its not rendering the theme border.  I have had all of this working on this same machine at one time with 6.10.  Any input would be appreciated thanks!

---

### Post by hidden_leaf_sasuke on 2007-08-01
hi..i actually had ATI MOBILITY RADEON x700 128 mb and beryl work like charm to me.But, now i'm using compiz fusion, its far more better than beryl and much more stable. I recommend you to use it. By the way, back there when i'm using beryl, i actually used xorg driver and DONT you EVER use the proprietary driver,it SUCKS so much! if you had installed it, u might had to remove it completely and just install the xorg driver..it much more better. If you want to install compiz fusion , head on to my blog (hiddenleafsasuke dot blogspot dot com). And just a reminder, it is best to use a fresh install ubuntu feisty and dont use another display driver, the default driver is the best.

---

### Post by gekkio on 2007-08-01
I also had the scrambled graphics problem with XGL and my X850XT, but I noticed it doesn't occur if I log in to an XGL session directly after reboot and never log out without rebooting.

Here's how I did it:

First I installed the latest fglrx drivers (the ATI proprietary ones from ati.com) using the build-pkg Ubuntu/feisty option and module-assistant. Remember to disable composite and the built-in fglrx in /etc/default/linux-restricted-modules-common.

My xorg.conf is mostly untouched, I simply used aticonfig --initial to set up everything.
Looks like I also put 
```
        Option      "UseInternalAGPGART" "off"
```
in xorg.conf Device-section. I can't remember why I did this but I think it was a fix for some problem which involved fglrx and PCI-E cards.
After this hassle I got working 3D acceleration with the latest fglrx.

Then I followed this guide
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

And boom! Compiz Fusion with desktop wall, expose and all the productivity increasing stuff. ;)
I use it daily at work, and so far I've had zero crashes or any real problems after the initial hassle.

I suggest you to ditch Beryl and go for Compiz Fusion as described in the guide. It's much more stable and even though Compiz in Treviño's repository is updated quite often (AFAIK they are svn builds), I've had no problems. Just remember that XGL might only work on the first login.

---

