---
title: "No console or Desktop after Feb 27 Updates"
date: 2016-02-28
forum: Desktop Environments
---

### Post by Stephen_Soliday on 2016-02-28
Has anyone experienced  trouble on reboot after Feb 27, 2016's daily update?
I am running 14.04.04 LTS with XUbuntu + NVidia 352.41
I have no console or  desktop. I can SSH in and I can replace "quite splash" with "text" in grub  to log on.
Rebuilding the NVidia driver and/or restarting the "lightdm"  service has no effect.
After booting in text mode, running "service lightdm start" goes to blank screen and locks out the console.
I can not recover with <ctrl><alt><F1> I have to ssh in from another computer and then "sudo shutdown"

---

### Post by egeezer on 2016-02-29
No idea whether this would work, but I would try startxfwm4 after booting in text mode - I think that the default might work.

---

