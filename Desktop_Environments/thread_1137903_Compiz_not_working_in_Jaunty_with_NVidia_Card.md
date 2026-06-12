---
title: "Compiz not working in Jaunty with NVidia Card"
date: 2009-04-26
forum: Desktop Environments
---

### Post by glennric on 2009-04-26
I just upgraded to Jaunty and now I can't get compiz to start.  I have a GeForce FX 5200, and have the nvidia drivers installed.  I downloaded the compiz-check script, and the script reports no problems.  Metacity's compositing is disabled.  However, when I type "compiz --replace" from the terminal I get 
/usr/bin/compiz.real (core) - Error: Another window manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
What is wrong?

---

### Post by andrea000 on 2009-04-26
I'm not running Jaunty but i had about the same problem with 8.10 ibex
first do you have proprietary drivers installed and do you have a integrated 
video card ati or Intel? Compiz sometimes picks up on the integrated card 
even if it's not beaning used.

---

### Post by glennric on 2009-04-26
andrea000:  As stated above I have an "NVidia" video card, with the nvidia (proprietary) drivers installed.  I do not have an ati or intel card (integrated or otherwise).

Anyway, I figured it out.  I had compiled and installed the nvidia 173.14.18 drivers in Intrepid, and when I upgraded it installed the nvidia 173.14.16 drivers that are the default in Jaunty.  This caused a conflict the set the default desktop window manager to metacity in gconf.  I changed that (and of course uninstalled the 173.14.18 drivers and reinstalled the 173.14.16 drivers) and now it works.  

Now I have rebuilt the 173.14.18 drivers for Jaunty and those are running fine.  I will put these in my ppa soon.  Hopefully these get included in Jaunty soon as the 173.14.16 drivers have some bugs that are rather annoying.

---

### Post by andrea000 on 2009-04-26
glade you found the problem

---

