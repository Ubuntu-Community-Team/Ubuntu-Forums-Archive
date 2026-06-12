---
title: "Compiling...."
date: 2005-05-16
forum: Desktop Environments
---

### Post by SmokingGun on 2005-05-16
What do i need to do to compile ipw2200 wireless drivers?  I have downloaded the build essentials and kernel source, unpacked it and made a symlink from it to 'linux' in /usr/src.  

When i type 'make' in ipw folder it says

"/lib/modules/2.6.10-5-386/build: No such file or directory"

What am i doing wrong?

---

### Post by nad on 2005-05-16
You need the kernel-headers package for your running kernel, unless you wish to build the headers from the kernel-source package (not necessary and not recommended unless you wish to learn a lot more).

---

### Post by SmokingGun on 2005-05-16
Thank you kind sir.

---

### Post by az on 2005-05-16
the kernel source is not configured.  You can do that or just install the linux-headers package and use that as your source tree....

---

