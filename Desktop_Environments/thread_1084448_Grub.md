---
title: "Grub"
date: 2009-03-02
forum: Desktop Environments
---

### Post by raunhar on 2009-03-02
I have a dual boot (Win XP with Ubuntu 8.10)

The current line up while booting is 
1. Ubuntu 8.10
2. Ubuntu 8.10 (Safe)
3
4
5. Win xP

How do i edit the settings so that the default boot option is Win XP .

please suggest

---

### Post by munishvit on 2009-03-02
sudo gedit /boot/grub/menu.lst

then change the following line
default   0
to 
default   4

---

