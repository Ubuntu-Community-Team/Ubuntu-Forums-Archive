---
title: "Software updater blues"
date: 2015-04-17
forum: Desktop Environments
---

### Post by nibal on 2015-04-17
I am using Ubuntu 14.04 x64. I have to use a custom kernel both 'cause of my Ethernet card (Realtek Gigabit) and my graphic card (ATI radeon R9 Saphire - need the fgrlx proprietary driver for it). The problem with Software Updater (SU) comes when new kernel images are in. Messes my /boot directory. I have to manually fix it and rerun update-grub each time. I know I can select off kernel images and headers, but SU doesn't go away unless i have installed everything. Is there a way to tell SU to fetch critical and security, but skip kernel updates?

TIA,

---

### Post by dino99 on 2015-04-17
i never use that buggy software, better satisfaction with synaptic

---

### Post by nibal on 2015-04-18
I removed update-manager and installed synaptic. I'm not sure they do the same thing. Synaptic is a graphical front-end to apt-get, which is different than update notifications given by the update manager. I am very comfortable with apt-get and don't need a graphical tool for it. Will synaptic notify me about needed security and critical upgrades?

On first glimpse it doesn't. While Software updater prompted me for updates in Ubuntu base, synaptic prompted me in updates for compiz. Am i missing smt?

---

