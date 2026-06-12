---
title: "X serve is disabled"
date: 2006-06-19
forum: Desktop Environments
---

### Post by Clarencemark on 2006-06-19
I am an idiot! I was playing around with the synaptic packager manager and looking at the various utilities for "Nvidia". I chosed to install the Nvidia x-config file and the one above it (the name escapes me). In order for the aforementioned to be installed, I was adivsed that "Nvidia glx" was going to be removed.

I am newbie - and I don't know what the "Nvidia glx" is. After installing and a reboot, I am no longer present with my graphical interface when Ubuntu 6.06 boot up. 

HELP!!!!! Please.

I am being informed that X server is disable and to restar GDM. I have no idea what these are.

---

### Post by Ramses de Norre on 2006-06-19
Try a ```
sudo aptitude update && sudo aptitude install -r nvidia-glx
``` from a tty (ctrl+alt+F1) then do ```
sudo /etc/init.d/gdm start
``` and hopefully it'll work again.

---

