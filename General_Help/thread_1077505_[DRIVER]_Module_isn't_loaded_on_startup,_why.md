---
title: "[DRIVER] Module isn't loaded on startup, why?"
date: 2009-02-22
forum: General Help
---

### Post by ramvi on 2009-02-22
I have compiled a driver and moved it to /lib/modules/KERNEL/drivers/net/vntwusb.ko

If I
```
sudo depmod -a vntwusb
```
then
```
lsmod
```
vntwusb doesn't show up.

**What are possible reasons for vntwsusb not showing up in lsmod?**
vntwusb also added to /etc/modules

Thanks for reading

---

### Post by ramvi on 2009-02-23
bump

---

