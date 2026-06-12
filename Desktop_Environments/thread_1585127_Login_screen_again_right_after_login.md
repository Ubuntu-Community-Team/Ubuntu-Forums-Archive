---
title: "Login screen again right after login"
date: 2010-09-30
forum: Desktop Environments
---

### Post by DanielVartanov on 2010-09-30
Hi!

Well, my problem is described in the topic: KDM starts normally, but if I enter correct password and hit 'enter', it shows black screen (for a second) and then restores login screen again.

The last two lines in kdm.log are following:
```
error setting MTRR (base = 0xd0000000, size = 0x10000000, type = 1) Inappropriate ioctl for device (25)
ddxSigGiveUp: Closing log
```

Also, I don't know if it's related, but I tried to install ATI Catalyst before it happened.

Lucid Lynx, 2.6.32-25-generic.

Thanks in advance,
Daniel.

---

### Post by P4man on 2010-09-30
Almost certainly related to the ATI drivers. Try this, boot in to recovery mode or access a TTY (control alt F1) and run this command:
```
sudo aticonfig --initial
```
then reboot (sudo reboot) and cross fingers.

If that doesnt work, tell us what videocard you have.

---

