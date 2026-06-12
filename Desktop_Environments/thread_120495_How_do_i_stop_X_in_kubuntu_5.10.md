---
title: "How do i stop X in kubuntu 5.10?"
date: 2006-01-22
forum: Desktop Environments
---

### Post by solarwind on 2006-01-22
Hi. How do i stop X in kubuntu 5.10? I am trying to install an Nvidia driver for my graphics card which requires me to first stop X.

How do i stop X in kubuntu 5.10?

All help is much appreciated. 
Thankyou.

---

### Post by jasmuz on 2006-01-22
Go to a console (ctrl+alt+f1) login and then type: sudo /etc/init.d/kdm stop

to restart it, sudo /etc/init.d/kdm start

---

