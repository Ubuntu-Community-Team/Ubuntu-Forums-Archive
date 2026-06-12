---
title: "Screensavers Not Working! (Kubuntu 6.10)"
date: 2007-04-07
forum: Desktop Environments
---

### Post by sleepingdragon on 2007-04-07
OK, I got a slightly weird problem here. Since the last nvidia update I've not been able to see my screensavers. The screen goes black as though the screensaver is about to start, but nothing happens. Moving my mouse or using the keyboard stops the screensaver as normal so nothing appears to be hanging. The only odd thing is that I can see them when I use the "TEST" function in the screensaver settings. From there, they work perfectly. 

All other 3D functions work well, there seem to be no glitches in games like Scorched3D, so I'm gonna guess that my nvid card is working OK.

Anyone got any ideas?

---

### Post by MontanaMax on 2007-04-07
I had problems with the base screensaver package a long time ago on my Kubuntu install, and switched out for the more feature rich** xscreensaver** package instead. It reads all the same screen savers, allows for a random screen saver to be launched instead of the same one every time, and has been rock-solid stable for me.

sudo apt-get install xscreensaver

Just need to put a link to it in the ~/.kde/Autostart directory to have it launch with each session.

Good luck!

---

### Post by FuturePilot on 2007-04-09
This is a bug in Edgy
[https://launchpad.net/ubuntu/+source/kdeartwork/+bug/70991]("https://launchpad.net/ubuntu/+source/kdeartwork/+bug/70991")
The workaround is to enable Power Saving. Open the System Settings menu and click on Screen and Monitor. Select the last tab that says Power Saving or something like that. Can't remember right now. Then check the box to enable it. The screen saver should work then. That's what worked for me.

---

### Post by michaelb322 on 2007-04-10
Can't remember where I saw the suggestion, but the fix for me was creating another user profile, logging in as the new user, and then switching back to the original user.  Since then, no problems with the screensaver even through reboots.  Weird bug. Do check out the other suggestions concerning the Power Saving though.

---

