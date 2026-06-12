---
title: "Usb mouse"
date: 2008-12-11
forum: General Help
---

### Post by pt.linux on 2008-12-11
Hi!

I installed ubuntu yesterday and it works fine. The only thing is that ubuntu doesn't detect my usb mouse, so at the moment I'm working with the touchpad but it will be useful to use the mouse for draws.

do I need to install something????

---

### Post by pt.linux on 2008-12-12
Please help!!!
I need my mouse

---

### Post by any.linux12 on 2008-12-12
Hi

try to mount your usb stuff
gedit /etc/fstab
and then write
usbfs          /proc/bus/usb            defaults      0       0

and be careful that you use <tab> and not space

---

### Post by pt.linux on 2008-12-12
Thanks. I don't know if it works but at least somebody answers me!

---

### Post by geefour on 2009-01-05
I've been having the same problem since I install Ultimate Edition 2.0 (Ubuntu Intrepid) over Ultimate Edition 1.8 (Ubuntu Hardy)

It is really annoying since I can't do anything in X with a problem like this. I have to switch to TTY1 just to do the sudo reboot command since I can't set up my WPA password to get connected.

---

### Post by fragos on 2009-01-06
I've never had this problem. Just plug in a USB mouse and it works. I even have a mouse, USB touchpad and Wacom tablet all connected at the same time with cursor control automatically going to whichever device when I start using it. Can "lsusb" see your mouse? Does unpluging and repluging fix the problem?

---

