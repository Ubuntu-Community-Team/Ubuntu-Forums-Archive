---
title: "How to disable synaptic touchpad on Ubuntu 7.10"
date: 2008-03-18
forum: Desktop Environments
---

### Post by Acunga on 2008-03-18
How to disable synaptic touchpad on Ubuntu 7.10 permanently?!!!I even deleted everything about touchpad in /etc/x11/xorg.conf but in vain, when I restart it fully functional!!:mad::mad::mad::mad:

---

### Post by Fire_Chief on 2008-03-18
Is this on a laptop? Do you need the touchpad for anything? If not, then try disabling it in the BIOS.

---

### Post by Acunga on 2008-03-18
No I cant disable it in the bios because I have to disable mouse also or set a serial mouse which makes biios start slowely while detecting the mouse.I need the OS to disable it.
By the way by deleting the drivers in xorg.conf my ubuntu has f*ked up again.Can I recover the file or reedit it somehow.I relly really really shoud have done a copy..reallly bad from my side...

---

### Post by Acunga on 2008-03-18
I fixed this by reconfiguring this so hwo can i disable the cursed touchpad?

---

### Post by deepclutch on 2008-03-18
^^^remove this:
```
sudo apt-get remove --purge xserver-xorg-input-synaptics
```
Hope this helps :p

---

### Post by Acunga on 2008-03-18
Is this the right command, i do nto find info on the google, what does it do, I hope only it does not remove the driver file again..

---

### Post by PurposeOfReason on 2008-03-18
Looks good to me although I would just configure the touchpad to disable while typing.

---

### Post by Acunga on 2008-03-20
e..
sudo apt-get remove --purge xserver-xorg-input-synaptics
should I restart  in order to disable the cursed touchpad?
Edit:This is some ****, it doesn't work at all

---

