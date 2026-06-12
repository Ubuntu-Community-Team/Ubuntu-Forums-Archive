---
title: "Need help with monitor"
date: 2009-04-21
forum: General Help
---

### Post by johnhdsi on 2009-04-21
Hi I am a fairly new user in Ubuntu and I was messing around with my settings to get WoW to work. Somewhere along the lines of tweaking I changed my video card settings so now I cant use advanced desktop settings and I can only boot into low graphics mode. After this happened I tried doing some tweaks and I messed up my monitor settings. Ubuntu login screen shows up correctly but when it boots into the desktop my screen goes crazy with diagonla lines and I cant see anything on the desktop. How can I change the setting back to the original monitor settings so I can see my desktop again? Please help me out with this I really don't want to re-install everything. Thanks in adavance


John

---

### Post by zman58 on 2009-04-21
Perhaps you can use the Live CD. Boot it and copy the /etc/X11/xorg.conf from it to a thumb drive. Use that as a starting point for your system. 

Remember to always back up a config file before making changes--it will save you time :)

---

### Post by johnhdsi on 2009-04-21
Thank you for the advice Ken,

I dropped my live cd in and it boots up fine and dandy. My question is twofold I guess. Can I copy the /etc/x11/xorg.conf file contents from the filesystem folder on the live cd desktop to the /etc/x11/xorg.conf file for my full install or do I do a specific area? I'm very new at Linux and have not done alot of tweaking (as obvious by my mistake), If I copy the xorg.conf file will it corrupt any of my other settings from my full install. I don't have a bunch of custom things and something tells me I should only cop the monitor setting area. If that is the case what would I be looking for? Is it a section labeled "Monitor"? I appreciate all the help with this problem.:D

John

---

