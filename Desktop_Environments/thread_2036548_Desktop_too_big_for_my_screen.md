---
title: "Desktop too big for my screen"
date: 2012-08-02
forum: Desktop Environments
---

### Post by abduljones on 2012-08-02
I've just installed ubuntu 12.04 on my desktop and the desktop continues past the bounds of my screen. Consequently, I can't  reach the menu on the left, though I can get the drop down menus if I ram the mouse up into the top right hand corner- so I can at least turn off and access system settings.
   
  The setting for display is stuck on "laptop" and there are no other options. The screen is a standard 10x12 ins (15ins diag) lcd. The graphics card is a PNY Geforce 6200 DDR2 512mb AGP. The graphics card has been working on the same system with windows with no issues.
 
 "Additional Drivers" shows NVIDIA aacelerated graphics driver (version 173) in use.

  Firstly, are there keyboard commands I can use, particularly to get Xterm up? And, secondly, where do I start?

In case you're wondering, I'm writing this on a laptop. 


Incidently, I have done nothing to the system since the install other than allow the 571 updates last night

---

### Post by mansonfan78 on 2012-08-02
> **abduljones said:**
> I've just installed ubuntu 12.04 on my desktop and the desktop continues past the bounds of my screen. Consequently, I can't  reach the menu on the left, though I can get the drop down menus if I ram the mouse up into the top right hand corner- so I can at least turn off and access system settings.
   
  The setting for display is stuck on "laptop" and there are no other options. The screen is a standard 10x12 ins (15ins diag) lcd. The graphics card is a PNY Geforce 6200 DDR2 512mb AGP. The graphics card has been working on the same system with windows with no issues.
 
 "Additional Drivers" shows NVIDIA aacelerated graphics driver (version 173) in use.

  Firstly, are there keyboard commands I can use, particularly to get Xterm up? And, secondly, where do I start?

In case you're wondering, I'm writing this on a laptop. 


Incidently, I have done nothing to the system since the install other than allow the 571 updates last night
Are you using the actual Nvidia driver (from their website)?  If so, the nvidia-settings app lets you set "overscan compensation" which should solve your problem.  I'm assuming you can't change the refresh rate?

---

### Post by abduljones on 2012-08-02
Won't let me do anything. As it's a wet day here and I hadn't put anything on 12.04 yet, I intalled 11.04 and that was fine. It even let me upgrade to the latest drivers for my card. Then I got a different disc for 12.04 and tried upgrading, but the installation got to rebooting after installing, gave me my disc back and then froze. Went off to do something else, came back, still frozen. Switched off, switched on, same problem, can't access launcher, can't get the dash up, also messages now re unknown error and it won't let me change anything on the nvidia drivers. Currently reinstalling 11.04, but I may do a fresh download of 12.04 and try again. I think I burned 2 different ISOs, but I may not have. There could be the same error on both discs.

  I'm also suspecting the dash is missing. If i make the settings really sensitive, I can get things off the launcher by clicking on the extreme right, but I can't get the dash. neither can I get it using the meta key or meta key combinations. I have, however, found out how to get the terminal up, and if I can get an internet connection, I might be able to post some more useful info about the system.
.

---

### Post by QIII on 2012-08-02
Was your first attempt at 12.04 an upgrade or fresh install?

The second time around seems to have been an upgrade attempt.

Did you remove the proprietary graphics driver prior to the upgrade?

One of the most direct routes to a failed upgrade is to forget to uninstall a graphics driver prior to the attempt.

This time, uninstall all proprietary drivers before upgrading.  You can reinstall them after the upgrade.

---

### Post by abduljones on 2012-08-02
No, first attempt was a clean install. Then clean install of 11.04, which was ok, then upgrade, on the off chance that the upgrade wouldn't upgrade what was causing the problem. Now I've put a clean install of 11.04, have been prompted to upgrade on line, which I did and the install currently looks good- though I'm puzzled as to whether this is an upgrade as I understand it, as it's still called 11.04, though its obtained 12.04 features. Or does the upgrade omit to upgrade the name. Or is it an 11.04 that got a bit of a face lift?
  If this is effectively a 12.04, then it may be the disc was the problem

---

### Post by mansonfan78 on 2012-08-02
> **abduljones said:**
> No, first attempt was a clean install. Then clean install of 11.04, which was ok, then upgrade, on the off chance that the upgrade wouldn't upgrade what was causing the problem. Now I've put a clean install of 11.04, have been prompted to upgrade on line, which I did and the install currently looks good- though I'm puzzled as to whether this is an upgrade as I understand it, as it's still called 11.04, though its obtained 12.04 features. Or does the upgrade omit to upgrade the name. Or is it an 11.04 that got a bit of a face lift?
  If this is effectively a 12.04, then it may be the disc was the problem
Actually, it just updated 11.04 to include it's most recent updates.  You can't upgrade 11.04 directly to 12.04, you have to upgrade to 11.10 first, then 12.04.  As to your disc problem(s); you could have burning issues with the software, your drive, or the discs.   You could try burning with a different program or brand of disc.  Although first, I'd try upgrading to 11.10 (in the update manager) and see if that goes smoothly.

---

### Post by abduljones on 2012-08-02
We're sorted . 11.04 may be a typo on my part, and yes, I'm sure you're right in that it was more of an update than an upgrade (the phrase upgrade was used, not update, so maybe it was to 11.10?). However, the online option to upgrade to 12.04 came with this evening's updates and I took it. When it rebooted, I had the same problem, but this time it allowed me to update the nvidia drivers to the most current ones and on rebooting after that, I now have a usable desktop. So thank you, everyone for your help. I will play with it tomorrow and see if I can get the video capture card to work with something. If not....I'll be back.

 Gosh, all this and a sack of gold medals... what a day

---

