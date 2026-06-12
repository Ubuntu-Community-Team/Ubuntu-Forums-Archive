---
title: "tty"
date: 2009-04-09
forum: General Help
---

### Post by boykadyot on 2009-04-09
Hi there,

It is possible to create new tty? Let say tty7? What I have right now are from tty1 to tty6. If it is possible, are there side effects?


thanks

---

### Post by KeyserSoze93 on 2009-04-09
Try running:

sudo /sbin/getty 38400 tty8

I'm not sure what the side effects are, though. A better way of doing it may be to go to /etc/event.d and copy the file tty1 to a file called tty8 (for however many you want), then open that file in a text editor and change any reference(s) to tty1 to tty8 (or whatever).

---

### Post by KeyserSoze93 on 2009-04-09
Try running:

sudo /sbin/getty 38400 tty8

I'm not sure what the side effects are, though. A better way of doing it may be to go to /etc/event.d and copy the file tty1 to a file called tty8 (for however many you want), then open that file in a text editor and change any reference(s) to tty1 to tty8 (or whatever).

EDIT: I say tty8, since tty7 does exist, and is used by xorg unless you have ubuntu server or whatever.

---

