---
title: "kernels"
date: 2005-08-27
forum: Desktop Environments
---

### Post by vladuz976 on 2005-08-27
hi how can i find out how many kernels i have installed other than to hit esc in grub. and how can i delete the ones i don't use?

---

### Post by dbcoder on 2005-08-27
apt-cache search linux-image
apt-cache search kernel-image

I believe those are the commands.  The first one is the stock kernel, the second command is for any kernels you have installed.


Simply apt-get remove KERNEL-NAME, the kernel name being what apt-cache spit out.


Just be careful.  Do not remove the stock kernel.  Just trust me on this one :P

---

### Post by arnieboy on 2005-08-27
[QUOTE=dbcoder]apt-cache search linux-image
apt-cache search kernel-image

I believe those are the commands.  The first one is the stock kernel, the second command is for any kernels you have installed.


Simply apt-get remove KERNEL-NAME, the kernel name being what apt-cache spit out.


Just be careful.  Do not remove the stock kernel.  Just trust me on this one :P[/QUOTE]
to avoid making mistakes, do the kernel removing bit from synaptic

---

