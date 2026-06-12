---
title: "Nvidia.ko"
date: 2005-03-15
forum: Desktop Environments
---

### Post by TheBlueCow on 2005-03-15
Ack, I just deleted my Nvidia.ko file (/lib/modules/kernel_version/kernel/drivers/video/nvidia.ko) because [this](http://www.ubuntulinux.org/wiki/BinaryDriverHowto) recommended it and now my mouse doesn't work anymore... is there anyway to rebuild it? Do I have to reinstall Ubuntu?

---

### Post by jdong on 2005-03-15
Run **apt-get install --reinstall linux-restricted-modules-(whatever version you have installed)**

---

