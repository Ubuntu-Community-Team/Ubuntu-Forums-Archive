---
title: "Ubuntu 17.04 black screen after logout"
date: 2017-07-27
forum: Desktop Environments
---

### Post by jamesjones01 on 2017-07-27
I'm running Ubuntu 17.04, have an Nvidia GTX 960 graphics card, and run the proprietary driver  (version 384.59 as of this afternoon; the problem appeared before the upgrade). When my computer boots up, the lightdm login screen appears, and I log in... but when I log out, the screen goes blank (more accurately: the login screen appears for an instant, the display goes totally black, and then goes to the "black as it can get while the LED panel has power" state). It happens whatever session I choose.

If I ctrl-alt-Fn over to another screen and switch back, there's the login screen, and I can log in again. ("ps -A | grep dm" while not logged in on the graphics screen shows four processes, three lightdm and one lightdm-greeter. When I am logged in graphically, all that shows up is two lightdm processes.

I've looked at the X log, and at the .xsession file and not seen anything that looks untoward, though I may well not have the knowledge to judge that accurately. Googling "ubuntu black screen after logout" turns up messages dating from 2012.

Has anyone had and solved this problem more recently than 2012? I once had a problem of this sort that turned out to be caused by having lightdm and another display manager running at the same time. Any advice or pointer to where to look next would be appreciated.

---

