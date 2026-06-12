---
title: "Automount in Enlightenment"
date: 2005-09-17
forum: Desktop Environments
---

### Post by Turtle.net on 2005-09-17
Hi,
I installed Enlightenment, based on Elive repository. Everything is working perfectly.

Under Gnome, when I plug my USB stick, the partition is automounted, and an icon appear on my desktop.

How can I do something similar in Enlightenment ?

---

### Post by Turtle.net on 2005-09-17
I think I have found something...
I created a new .eapp file with e_utils_eapp_edit gnome-volume-manager.eapp, with just the command gnome-volume-manager and I put this new .eapp in startup and restart using Entangle...

And you know what .... when I plug my USB stick a nautilus windows appear with the content of my usb stick (just as usual in Gnome).

---

### Post by psychicdragon on 2005-09-18
Yup,

If you don't like that behaviour. ie. the new nautilus window opening you can disable it or change the default action with the gnome-volume-properties applet.

---

### Post by Turtle.net on 2005-09-18
Thanks,
I'll try to open evidence instead of nautilus

---

