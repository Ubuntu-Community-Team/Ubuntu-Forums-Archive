---
title: "How to upgrade and patch the 2.6.27.10 kernel"
date: 2009-01-31
forum: General Help
---

### Post by tarekeldeeb on 2009-01-31
Hello all,

I have a 64-bit ubuntu 8.10 with all upgrades (kernel = 2.6.27.9), and I have  dvb-s pci card. It is listed ([here]("http://www.linuxtv.org/wiki/index.php/DVB-S_PCI_Cards")) not included in the v4l, but there is a patch (same link) for my dvb-s (Twinhan 1027) for kernel  2.6.27.10.

So I want to download kernel >> patch >> install/upgrade

I'm current;y downloading the kernel source:
```
 cd /usr/src && wget http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.27.10.tar.bz2

```

what should be the next step ?

Thanks in advance,

Tarek

---

### Post by dcstar on 2009-02-01
> **tarekeldeeb said:**
> Hello all,

I have a 64-bit ubuntu 8.10 with all upgrades (kernel = 2.6.27.9), and I have  dvb-s pci card. It is listed ([here]("http://www.linuxtv.org/wiki/index.php/DVB-S_PCI_Cards")) not included in the v4l, but there is a patch (same link) for my dvb-s (Twinhan 1027) for kernel  2.6.27.10.

So I want to download kernel >> patch >> install/upgrade

I'm current;y downloading the kernel source:
```
 cd /usr/src && wget http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.27.10.tar.bz2

```

what should be the next step ?
........

The next step is to search out the many detailed (and lengthy) HOWTOs on compiling and installing kernels. It is not a trivial process.

---

