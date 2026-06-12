---
title: "New ATI driver install"
date: 2005-08-28
forum: Desktop Environments
---

### Post by KingBahamut on 2005-08-28
I believe ive done everything that the guides say, but Im not getting any decent accel out of this 9600. Has anyone had success with the new driver installer? 

And what the heck am I doing wrong. 

When I tried to do the install, it gave me errors, when I tried to generate a dist specific package it gave me errors. When I get the box up again, Ill cross post the fglrx logs.

----------------------
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.
--- from fglrx-install.log 

Is this because kernel headers arent installed? or is it utterly something more idiodic than that. 

Thanks guys.

---

### Post by drizek on 2005-08-28
you need kernel modules.

---

### Post by KingBahamut on 2005-08-28
which packages specifically then. 

linux-headers-<kernel version here>??

---

