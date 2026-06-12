---
title: "Latest Kernel Headers in apt?"
date: 2005-12-23
forum: General Help
---

### Post by Milton on 2005-12-23
I'm trying to get vmware installed however it wants to compile a module however it can't find the header source files for the current kernel, the error message I get is:

> The directory of kernel headers (version 2.6.11) does not match your running kernel (version 2.6.12-10-386).  Even if the module were to compile successfully, it would not load into the running kernel.

the version of the kernel headers in the apt repository is 2.6.11, is this expected to be upgraded to be inline with the latest kernel which updated this morning for me?

If not, how can I get the correct version of the kernel headers?

---

### Post by darth_vector on 2005-12-23
```
sudo apt-cache search linux kernel headers
```

brought up the following:

linux-headers-2.6.12-9-386 - Linux kernel headers 2.6.12 on 386
linux-headers-2.6.12-10-386 - Linux kernel headers 2.6.12 on 386
linux-headers-386 - Linux kernel headers on 386

as well as the 686 and k7 versions and a whole lot of other junk. i think the second one is the one your after.

---

### Post by Milton on 2005-12-23
damn, that's a bit embarrassing :(

---

### Post by darth_vector on 2005-12-23
lol, it happens. dont worry about it :)

---

