---
title: "Installing Emerald Causes Laptop Crash"
date: 2007-12-03
forum: Desktop Effects &amp; Customization
---

### Post by zeller on 2007-12-03
Compiz-Fusion is working wonderfully on my HP zd8000 laptop after much frustration. I had been trying to figure out why it was crashing.

After numerous attempts to get it working and many re-installs of Ubuntu when it hosed my system entirely I narrowed the problem to the installation of Emerald.

Excerpt from a thread started by chris.m.ball:
> SOLUTION (that worked for me at least):
1. Backed up my /usr/bin/compiz
2. Edited it and commented out the following line:
"#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700"
3. Reboot my machine, went to the "Appearance" tool and voila - I was finally able to select whatever level of compiz-fusion I would like.

The unfortunate thing here is that everyone facing these issues will likely go down ALL of the roads I did and burn countless hours in frustration, only to realize they have the correct drivers and this is an issue with one of the patches, particularly with the incorrect blacklisting for compiz.

Upon following that solution, everything has worked hunky-dory for over 24 hours of uptime. Amazing. Then I installed Emerald. 1-2 minutes later, zowy, the laptop just turns off. No shutdown procedure. No warning. Quick as a blown lightbulb it turned off.

Uninstalled Emerald once I rebooted. Luckily it didn't turn off quicker than I could uninstall. Haven't had a problem since I uninstalled it.

What might be the problem? What log file should I look at? What .conf file would I be able to change, if at all? I really like Emerald and hope I can use it.

Please and thank you.

---

### Post by zeller on 2007-12-13
Bump. Anyone know how to get Emerald working?

---

### Post by zeller on 2008-01-24
Just wondered if anyone else encountered this problem? What steps can I take to find out how to fix this? I know not where to look other than the xorg config file and I don't even know what to look for in that that might be related.

---

