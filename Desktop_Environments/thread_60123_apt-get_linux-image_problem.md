---
title: "apt-get linux-image problem"
date: 2005-08-26
forum: Desktop Environments
---

### Post by dajomu on 2005-08-26
Got this message when running apt-get upgrade:

```
Unpacking replacement linux-image-2.6.10-5-386 ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.4_i386.deb (--unpack):
 trying to overwrite `/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.10-5-386
dpkg-deb: subprocess paste killed by signal (Broken pipe)
```

```
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Anyone know the reason for this?

DaJoMu

---

### Post by az on 2005-08-26
You made the ndiswrapper modules package by hand, eh?

REmove it, install the new kernel and then recompile it.  Actually, remove ndiswrapper-utils, too (the one you made by hand) and install the stock ndiswrapper-utils from Hoary.  The modules are already included in the stock kernel.

Unless they did not work in the first place, try just running the stock ndiswrapper.

Otherwise, just recompile and install them.

---

