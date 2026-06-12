---
title: "dpkg-reconfigure xserver-xorg doesn't work"
date: 2005-10-12
forum: Desktop Environments
---

### Post by bugmenot on 2005-10-12
Hi, today I was messing around with some nvidia drivers and after I restarted xserver wouldn't boot, the error log was blank. I tried the reconfigure command but it says it's broken or not fullly installed. Please help me!

---

### Post by bugmenot on 2005-10-12
Actually I have a xorg.conf backup. But how do I use it?

---

### Post by az on 2005-10-12
boot into recovery mode
apt-get update
apt-get -f install
apt-get install x-window-system-core linux-restricted-modules nvidia-glx
dpkg-reconfigure xserver-xorg
nvidia-glx-config enable
init 2

---

