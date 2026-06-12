---
title: "Screen Saver Crashing System"
date: 2006-01-27
forum: Desktop Environments
---

### Post by SychoSly on 2006-01-27
I have Ubuntu 5.10 installed. Everytime the system sits and the screen saver goes on the system crashes and I can't do anything only pull the cord to reboot.

When I reboot and try to go to the preferences > Screen Saver section that freezes th computer as well and also have to pull the plug.

Is there a way to turn off the screen saver through the terminal?

Thanks.

---

### Post by bikeboy on 2006-01-27
In the terminal enter "Top". This will list the current processes. Press "u" and then enter your username. Look for the "xscreensaver" process and check out its PID (in the very left column). Press "q" to exit Top.

When back at the terminal type "kill ####" where #### is the PID of Xscreensaver.

This is only a temporary fix as it will reload at startup, but at least it gives you a start so you can troubleshoot some more.

---

