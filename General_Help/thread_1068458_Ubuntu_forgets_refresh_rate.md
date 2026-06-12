---
title: "Ubuntu forgets refresh rate"
date: 2009-02-12
forum: General Help
---

### Post by kdxensen on 2009-02-12
Ubuntu 8.10 64 bits, Nvidia 6200, nvidia driver 1.77. Boots at 60hz refresh rate. Launch nvidia xserver config utility and reset to 85 hz, but have to do this every boot. How come?

---

### Post by dcstar on 2009-02-12
> **kdxensen said:**
> Ubuntu 8.10 64 bits, Nvidia 6200, nvidia driver 1.77. Boots at 60hz refresh rate. Launch nvidia xserver config utility and reset to 85 hz, but have to do this every boot. How come?

All this stuff is autodetected at startup unless there is something manually set in your xorg.conf file to override things.

What is in your /etc/X11/xorg.conf ?

---

