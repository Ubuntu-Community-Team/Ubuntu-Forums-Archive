---
title: "Different login screens, screen blank"
date: 2015-04-17
forum: Desktop Environments
---

### Post by orion_134 on 2015-04-17
I'm having several issues with my 14.04 LTS on a Dell M4500, they may be related.  
1) It was having the ever-popular issue of the auto-lock not working, thus the auto-screen power-off wasn't working to turn off my screen once the timer locked the computer. 
2) Sometimes on reboot or even resume, the screen is backlit (yet blank) and the keys are responsive, it just wasn't sending signal to the screen.  Sometimes shutting the lid will hibernate it then it will be fine on resume.
3) A sudo reboot or hard reboot it takes me to a 2d blue "swipe" screen to login, then a grey screen to enter credentials.  On a normal reboot from shell, it takes me back to the purple login screen.

I tried reading up about different display managers so I installed one, but I can't remember what it is.  I think the problem may be a confliction of screensavers/lock properties, but I'm not sure.

Ideas?

---

### Post by orion_134 on 2015-04-18
Also, sometimes when rebooting, the screen goes a "frazzled" white before shutdown.

---

### Post by Vladlenin5000 on 2015-04-18
Hi and welcome.

A Dell Precision M4500 has a Nvidia Quadro FX 880M or 1800M. Either benefit from current Nvidia proprietary drivers. You can start by going to System Settings >> Software & Updates. Select the rightmost tab, Additional drivers, and check what's being offered. You probably want the proprietary driver with the highest version number which for 14.04 should be 331. Test it and if it still has issues then you need to install, using a different method, at least Nvidia 340.xx which is the recommend long term driver by Nvidia.

---

### Post by orion_134 on 2015-04-19
Mine has the 880M and was running the open source driver.  I switched to the proprietary (tested) driver and we'll see how it goes.

Thanks!

---

