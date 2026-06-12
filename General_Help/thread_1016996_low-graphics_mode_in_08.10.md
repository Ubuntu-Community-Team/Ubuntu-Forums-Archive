---
title: "low-graphics mode in 08.10"
date: 2008-12-20
forum: General Help
---

### Post by Sparkster185 on 2008-12-20
FYI:  This is being done on a Toshiba Satellite, don't know the model number exactly.  Can provide if it will help.

I was able to install 08.10 just fine a week ago.  But I forgot to set my /home mount to my second HDD.

Rather than just fixing the mount point, I just decided to re-install and set my second HDD as the mount point for /home.

Since then I've been getting the error:

<b>Ubuntu is running in low-graphics mode</b>
The following error was encountered.  You may need to update your configurations to solve this.

(EE) GARTInit: Unable to open /dev/agpart (No such file or directory)
(EE) [drm] drmOpen failed
(EE) intel(0): [dri] DRIScreenInit failed.  Disabling DRI
(EE) intel(0): Failed to allocate famebuffer.  Is your VideoRAM set too low?
(EE) intel(0): Couldn't allocate video memory.





I've tried re-installing twice now and it produces the same results.  Should I just re-install and forget about my /home mount and do it manually?

Thanks.

---

### Post by Sparkster185 on 2008-12-20
I just re-started using the previous version of my kernel and it's working fine.  Obviously something is not right.  I have no idea what has changed since the previous release.

---

