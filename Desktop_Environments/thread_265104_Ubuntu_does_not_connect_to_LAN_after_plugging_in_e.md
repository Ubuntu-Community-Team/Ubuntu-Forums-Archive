---
title: "Ubuntu does not connect to LAN after plugging in ethernet"
date: 2006-09-25
forum: Desktop Environments
---

### Post by littlewing0906 on 2006-09-25
Quick question: Sometimes I boot my laptop into Ubuntu all the way to the desktop, and I forget to plug my ethernet cable into the laptop.  Starting my laptop with the ethernet cable plugged in gets me connected to the internet with no problem.  But if I plug in the ethernet cable after booting, I can't get on.

Once I plug the ethernet cable in, how can I get ubuntu to redetect the network settings and get on the internet?

---

### Post by lagagnon on 2006-09-25
try "sudo ifconfig eth0 up" (if the interface is eth0, check to make sure it is before you do this).

---

