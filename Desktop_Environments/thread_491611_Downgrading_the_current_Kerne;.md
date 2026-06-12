---
title: "Downgrading the current Kerne;"
date: 2007-07-03
forum: Desktop Environments
---

### Post by ppan on 2007-07-03
All, I am new to Ubuntu. I installed it on my lapto just the other day. The version of the running kernel on my machine is 2.6.20-16-generic #2 SMP. However, there is an app that I use all the time a Cisco VPN client which according to their support docs :

The VPN Client for Linux supports Red Hat Version 6.2 Linux (Intel), or compatible libraries with glibc
Version 2.1.1-6 or later, using kernel Versions 2.2.12 or later.
Note The VPN Client for Linux does not support kernel Version 2.5 or SMP (multiprocessor) kernels.

I would therefore have to downgrade my kernel in order to use the software. How do I do that?

Thanks

---

### Post by Vajra Vrtti on 2007-07-03
I don't know for sure but maybe kernel 2.6.20-16-386 is not SMP.
Install package **linux-386** with Synaptic and it will be added as another option in the grub boot menu.

---

