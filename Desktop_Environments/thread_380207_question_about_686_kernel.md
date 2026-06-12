---
title: "question about 686 kernel"
date: 2007-03-09
forum: Desktop Environments
---

### Post by nephish on 2007-03-09
lo there,
i just did an apt-get install linux-686

when the computer rebooted, i did uname -r and got this
2.6.17-11-generic

apt-cache show linux-686 says that the package is only for upgrades
Package: linux-686
Priority: optional
Section: restricted/base
Installed-Size: 52
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 2.6.17.10
Depends: linux-generic


so my question is, do i have the 686 kernel running now ? 
thanks

---

### Post by mcduck on 2007-03-09
There is no separate 686 kernel in Edgy, the generic kernel detects your CPU(s) at boot and enables different optimizations accordingly. The package you see in repos is just empty metapackage pointing to the generic kernel, to help upgrading from 6.06 to 6.10. :)

---

### Post by nephish on 2007-03-09
ok, well cool
thanks

---

