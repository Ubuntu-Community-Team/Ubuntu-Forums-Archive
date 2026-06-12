---
title: "screen resolution refresh rate"
date: 2005-09-05
forum: Desktop Environments
---

### Post by fartbarker on 2005-09-05
Everytime I restart my comp the screen resolution reverts back to 1280 x 1024. How can I keep it on 1024 x 768?

Also, how can I change the refresh rate? The only option available is 76 Hz. I've tried editing the key in the configuration editor but it doesn't work.

---

### Post by plb on 2005-09-05
either dpkg-reconfigure xserver-xorg
or edit /etc/X11/xorg.conf manually

---

