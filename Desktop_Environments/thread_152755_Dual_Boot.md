---
title: "Dual Boot"
date: 2006-03-30
forum: Desktop Environments
---

### Post by phelixnyc on 2006-03-30
I have to drives in my pc, xp installed in one, ubuntu in the other. Is there a way to choose which os(hdd) to boot to once I boot my pc?

---

### Post by mustang on 2006-03-30
Post your /boot/grub/menu.lst

---

### Post by Ramses de Norre on 2006-03-30
Have you installed grub? If so you should get a menu when booting.
If you mean the one booted automaticaly: there is a line in /boot/grub/menu.lst "default: x" and you can change x in the number of the operating system, counting from top and starting at 1.

---

### Post by phelixnyc on 2006-03-30
Im wondering is it easier to have one drive dual boot?

---

### Post by frizzl on 2006-03-30
well if you installed using grub, after your computer goes through the POST (Power On Self Test) it will get to a menu that lets you select Ubuntu or Windows.

if you didnt use grub im not sure what to do :/

if you did use grub go to /boot/grub/menu.lst
and in there you can edit the menu.

---

