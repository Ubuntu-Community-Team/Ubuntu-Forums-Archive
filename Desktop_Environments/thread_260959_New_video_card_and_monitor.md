---
title: "New video card and monitor"
date: 2006-09-19
forum: Desktop Environments
---

### Post by GQed76 on 2006-09-19
I got a new video card and monitor.  How do I update ubuntu, specifically Xorg that i have a different card and Monitor.  My resolution rates are wrong for example

---

### Post by croak77 on 2006-09-19
You can edit /etc/X11/xorg.conf and put in the correct values or run sudo dpkg-reconfigure xserver-xorg and go through the questions.

---

