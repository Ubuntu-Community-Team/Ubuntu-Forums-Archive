---
title: "Nvidia Twinview - Maximising across both screens"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by PureLoneWolf on 2007-10-27
Hi all

I can't seem to get it working properly.  I was recommended to use Envy to get the latest drivers etc which just seemed to completely mess things up.  It took me ages to tell envy to use the 96.43.01 Nvidia drivers.  This got the machine up and running again with the 2 screens available in the resolutions I wanted.

This gets me back to the issue I was having last night.  The main panel extends across onto screen 2 (meaning the clock/logoff etc are over there), not a problem in iteself, but I would prefer that the screens were treated independently as in XP.

When I maximise anything, it maximises over both screens, which essentially blows out full screen video etc.

Someone in another thread mentioned disabling visual effects, this hasn't helped the issue.

I have attached my xorg.conf in case anyone can help.

Setup:
Nvidia GeForce 6800 Ultra
Samsung SyncMaster 930bf TFT- Should be screen 1 on the left - 1280x1024
Mobi 15" TFT - Should be screen 2 on the right (Interestingly, this is picked up as a CRT) - 1024x768

The other thing I noticed was that at the beginning, the Mobi was being used as the default screen and it took a lot of messing to get it the other way around.

All help is very much appreciated

---

### Post by PureLoneWolf on 2007-10-27
Sorted it 

Added:   Option "Xinerama" "false"

to the serverlayout section of xorg.conf and I can now maximise to the window I am on.

Seems to be fine

---

