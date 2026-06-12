---
title: "I need to Reinstall and configure Grub"
date: 2006-07-21
forum: Desktop Environments
---

### Post by inf4my on 2006-07-21
how can I reinstall and configure grub from a livecd without having to reinstall ubuntu.

---

### Post by neouser99 on 2006-07-21
easiest way use the livecd and boot into rescue mode on the root directory. essentially, you want to run the grub-install command from a chroot on your main / partition, which will use the grub.conf stuff you already have installed on the hard disk. if this doesn't make sense then come back and i can go a little more in depth.

-neo

---

