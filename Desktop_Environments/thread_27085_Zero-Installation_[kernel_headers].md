---
title: "Zero-Installation [kernel headers]"
date: 2005-04-14
forum: Desktop Environments
---

### Post by Synnergy on 2005-04-14
I'm trying to install Zero-Installation, which requires 'lazyfs'.  I've downloaded the source for that, but when going through the configure I come across the following error:

```

The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux). Note: this error could also mean
that you haven't built the kernel yet.

```

I have installed the package 'linux-kernel-headers' - but this doesn't seem to make any difference.  I did a search on my machine for this file and came across '/usr/include/linux/version.h' but I don't think this is correct.

First time I've tried to do anything with the kernel, and I'm a bit worried I'm going to do something real bad :)  Can someone just point me in the direction of some good resources maybe?  I've done some looking around, but most of what I can find seems real old, or specific to one distribution or another.  I'm not confident I know all the differences between them to pick/choose what I need to follow :)

Thanks for any direction!

---

### Post by wfx on 2005-04-15
test this:
apt-cache search linux-headers-$(uname -r)

if it find it then you can make
apt-get install linux-headers-$(uname -r)

---

### Post by Synnergy on 2005-04-16
[QUOTE=wfx]test this:
apt-cache search linux-headers-$(uname -r)

if it find it then you can make
apt-get install linux-headers-$(uname -r)[/QUOTE]
 That worked great - thanks for the help!

---

### Post by wfx on 2005-04-16
You are welcome :-)

---

