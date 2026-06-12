---
title: "help xfce"
date: 2015-04-14
forum: Desktop Environments
---

### Post by mariosminer on 2015-04-14
deleted  xfce and i had auto login on and it gives me "could not load xfce session" in a black screen



please if anyone knows a solution ??????

---

### Post by dino99 on 2015-04-14
you are ready to install again;)

---

### Post by ajgreeny on 2015-04-14
What do you mean by "deleted  xfce"?
Did you add the xfce DE to a system with another DE, eg Ubuntu with unity, then setup your autologin, or was autologin already working?

Let's see the output of ```
cat /etc/lightdm/lightdm.conf.d/10-xubuntu.conf
``` to see if that is how your autologin is configured; we can then try to figure out how to overcome this for you.  However, we need to know a great deal more detail about what exactly you've done; what you added to your system, what you deleted, when you setup the autologin etc etc.

---

### Post by louis077 on 2015-04-14
I would boot to recovery and reload XFCE from there. Think you just have to hold the "Shift" key down after bios boots to bring up GRUB.

---

