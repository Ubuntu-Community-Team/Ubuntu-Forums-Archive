---
title: "Audio driver config asking for /usr/src/linux/version.h"
date: 2005-12-29
forum: Desktop Environments
---

### Post by ryan76 on 2005-12-29
Hi, I'm having a problem with sound on one DVD only. I thought it prudent to install the correct sound driver for my soundcard which is the ALC655 codec, according to computer's documentation.

I downloaded the driver: alc-112803.tar.bz2, I ran ./configure but this comes up:

```
checking for directory with kernel source... /usr/src/linux
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
```

The only thing in that folder is a folder called rpm.

Can anyone help please?

---

### Post by Susana on 2005-12-29
you need build-essential, kernel-package and linux-headers-`uname -r`

---

### Post by ryan76 on 2005-12-29
Many thanks, that worked great. Make also asked for gcc-3.4.

Cheers!

---

