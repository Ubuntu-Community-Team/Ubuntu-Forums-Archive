---
title: "Kernel location in Ubuntu?"
date: 2006-10-05
forum: Desktop Environments
---

### Post by OpticalIllusion on 2006-10-05
So, isn't the kernel supposed to be located in the /usr/src/linux directory?

I upgraded from the default kernel to the 686 kernel and I don't even have a /usr/src/linux directory.  Where can it be located?

---

### Post by uros678 on 2006-10-05
Hey,

my guess would be it's in /boot. The /usr/src/linux dir is where the sources for the kernel go... I think.. :-k 

best regards,
uros

---

### Post by angustia on 2006-10-05
the kernels are any vmlinuz-*** under /boot

and modules are under /lib/module/VERSION, where VERSION is the version number of the kernel.

in /usr/src/ are the sources of the kernel, can be many version, and /usr/src/linux is just a shortcut to one of them

---

