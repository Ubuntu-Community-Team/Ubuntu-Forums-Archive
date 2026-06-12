---
title: "No proper shutdown"
date: 2012-03-08
forum: Desktop Environments
---

### Post by delvinjosedeu on 2012-03-08
I installed kubuntu11.10 in my laptop(only os). The problem is that in some cases if i shutdown the machine it won't. If i click on the shutdown symbol screen is turning into a dull display with the same desktop background till i forcefully shutdown the system using power button. Anybody know the reason? pls help..?

---

### Post by cespinal on 2012-03-08
Try this: 

> 
  a.Open Terminal
  b. Run this command:
     kdesudo kate /etc/kde4/kdm/kdmrc
  c. Edit and change "#TerminateServer=true" to "TerminateServer=true". Save the file.

---

### Post by delvinjosedeu on 2012-03-09
defnitly i will try this. Thanks for the help. Do u know how to enable finger print detection in kubuntu11.10(HP probook 4430)

---

### Post by Zorael on 2012-03-10
As a sidenote, if this only happens when rebooting is may be caused by the kernel trying to reboot by simulating a reboot button keypress, which laptops seldom have. If your bios doesn't accept that the system will just halt.

See [this blog post](http://linux.koolsolutions.com/2009/08/04/howto-fix-linux-hangfreeze-during-reboots-and-restarts/).

I'm unsure if this has any effect on shutdown whatsoever; just thought I'd mention it.

---

