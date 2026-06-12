---
title: "Wireless problem"
date: 2010-01-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ehagel on 2010-01-05
I can not make the wireless to work on my dell inspiron mini.
Im using Ubuntu 9.10 netbook remix. when I start from the live usb, and I select the option of using ubuntu without making any changes on my computer, it works perfectly after installing the rescritcted drivers, but once I installed ubuntu on my computer, it doesnt work any more.

I have already install the bcmwl-kernel-source and the driver too. And it doesnt works.
When I try to activate it from the sistem - administration menu, it appears an  error with details in the file: /var/log/jockey.log when I opened thats what it says:

2009-12-30 23:10:23,365 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2009-12-30 23:10:23,607 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2009-12-30 23:10:23,698 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2009-12-30 23:10:26,842 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2009-12-30 23:10:30,465 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2009-12-30 23:10:30,467 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2009-12-30 23:10:30,530 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

I dont know that to do.
Thanks

---

### Post by again617 on 2010-02-09
I am having the same problem but only when I happen to boot into one of the pae kernels.

---

### Post by coffeeaddict22 on 2010-02-10
Hi,
Need a wee bit more info.
Did you have XP installed?  And was the wireless working in XP if you did?
Can you open a terminal (Applications/Accessories/Terminal), type in the following 3 (separate) commands : ```
lsmod
nm-tool
lshw -C Network
``` and post back the output?

---

### Post by KegHead on 2010-02-10
Hi!

I had numerous problems on my mini 9 w/9.10 after an update.

It cleared up after a few days on it's own.

Wifi is working fine.

KegHead

---

