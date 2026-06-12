---
title: "I broke GDM. Need to reset it to defaults or change config"
date: 2007-04-26
forum: Desktop Environments
---

### Post by weblordpepe on 2007-04-26
Hello guys. This problem is stopping me logging in.

Somewhere in the 'Login Window'  icon I ticked a box (I forgot what) and now whenever I reboot, I dont get the normal Ubuntu login screen, but I get the XDMCP chooser window straight away. I cannot exit this screen.

As such I cannot log into my machine locally.

Please let me know how I can reset my GDM to defaults or just let me log into my machine as normal. I do not understand how gdm.conf works.:confused: 

Oh yeah aside from this, UBUNTU RUELZ!!! :guitar:

---

### Post by weblordpepe on 2007-04-26
..bump!

---

### Post by Compyx on 2007-04-26
Looking at my /etc/gdm/gdm.conf, there's a line (271) that says '[xdmcp]', a few lines below that, there's a line 'Enable=false'. My guess is that your gdm.conf has 'Enable=true', so perhaps changing that line might solve your problem.

---

