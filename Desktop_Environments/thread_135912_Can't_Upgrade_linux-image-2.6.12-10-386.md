---
title: "Can't Upgrade linux-image-2.6.12-10-386"
date: 2006-02-24
forum: Desktop Environments
---

### Post by AlphaMack on 2006-02-24
I get this error in Synaptic package manager:


E: /var/cache/apt/archives/linux-image-2.6.12-10-386_2.6.12-10.28_i386.deb: trying to overwrite `/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.12-10-386

I tried deleting the ko file but I still get the error.  Any ideas on how to fix this?

---

### Post by o_fortuna on 2006-02-24
[QUOTE=alphasubzero949]I get this error in Synaptic package manager:


E: /var/cache/apt/archives/linux-image-2.6.12-10-386_2.6.12-10.28_i386.deb: trying to overwrite `/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.12-10-386

I tried deleting the ko file but I still get the error.  Any ideas on how to fix this?[/QUOTE]
Try, at the command line (Applications-->Accessories-->Terminal):
[CODE]sudo apt-get dist-upgrade[CODE]
That *should* take care of your problems. No guarrantees, but it should automatically fix any problems.

---

### Post by AlphaMack on 2006-02-24
Thanks.  I simply reinstalled ndiswrapper.

---

### Post by LateNighter on 2006-02-24
The above suggestion should Work.

 I didn't have that problem when I installed it Automattically did it for me,
 Go Figure.:rolleyes: 

 If all else Fails Reinstall and that Should cause it to Upgrade by itself, At least thats whats worked for me.  Good Luck...

---

