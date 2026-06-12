---
title: "Multiple Kernels"
date: 2006-05-18
forum: Desktop Environments
---

### Post by VortexICS on 2006-05-18
Hey guys, after a fresh install of 5.10 and the automatic update of the kernel, I see the old and the new kernel in GRUB. Besides changing the grub.conf file, do I need to keep the old kernel for something ? What's your advise on that ? 

Thanks!

---

### Post by bluevoodoo1 on 2006-05-18
You can keep it just in case something happens that makes your current kernel unbootable. 

or

If you remove it with synaptic (the linux-image and headers for that kernel) it will adjust your grub configuration automatically and give you some extra space on your disc!

(I personally rid myself of the old kernel after a few days-- to make sure the newest one doesn't give me any problems)

---

### Post by VortexICS on 2006-05-20
Thanks dude, I was afraid to mess my system up if I did that.

---

