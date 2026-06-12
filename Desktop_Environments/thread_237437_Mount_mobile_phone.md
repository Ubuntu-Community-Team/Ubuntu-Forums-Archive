---
title: "Mount mobile phone"
date: 2006-08-16
forum: Desktop Environments
---

### Post by chloraldo on 2006-08-16
I have a Sony Ericsson K800i. When I plug it in using USB I get a link on the desktop. Perfect.

But: It's mounted as root and doesn't let me change that. Any ideas?

---

### Post by Lunar_Lamp on 2006-08-16
I'm not entirely sure, but I think you may need to fiddle with your /etc/fstab for this.

Add an entry for the phone in the /etc/fstab with the settings that you want, then when it is detected it will mount as such.

---

### Post by chloraldo on 2006-08-16
> **Lunar_Lamp said:**
> I'm not entirely sure, but I think you may need to fiddle with your /etc/fstab for this.

Add an entry for the phone in the /etc/fstab with the settings that you want, then when it is detected it will mount as such.

Would that be something like this?
```
/dev/sdb1       /media/phone     vfat    defaults        0       0
```

---

### Post by Lunar_Lamp on 2006-08-16
Something like that yes, but I'm afraid I don't know fstab well enough to be confident of giving you an answer, nor if/what options are required to mount as user as opposed to root (I think you may need to put 'user' after default: "defaults,user")

---

