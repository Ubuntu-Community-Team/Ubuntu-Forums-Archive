---
title: "help cant get 1920x1280"
date: 2005-09-19
forum: Desktop Environments
---

### Post by frostnova on 2005-09-19
hi guys, just installed kubuntu.. and im having trouble getting my widescreen resolution set to 1920x1280.. I can however get 1920x1200 but thats to low for my native resolution on this monitor.. can any of you tell me what i should be doing.. I dont see that resolution in the xserver config. ](*,)

---

### Post by mlomker on 2005-09-28
Not sure if your question got answered elsewhere, but the linux video drivers seem to prefer square screens.  I'm not sure if you have nvidia or ATI, but it may require creating a custom modeline to get the right resolution.  It's also possible that the monitor is reporting the wrong capabilities to the driver.

The /var/log/xorg.0.log is the place to start looking.

---

