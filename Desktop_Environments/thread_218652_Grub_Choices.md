---
title: "Grub Choices"
date: 2006-07-18
forum: Desktop Environments
---

### Post by mpierce on 2006-07-18
By default, grub should load without my pressing Esc to see the menu.

It is not doing that rather, it is just loading the default kernel.

How do I repair this?

---

### Post by llamakc on 2006-07-18
Do you want the grub menu to load by default? Grub is loaded, and if your computer boots into a kernel, it works properly.

In the file /boot/grub/menu.lst you can edit the line and comment out:

hiddenmenu 

and then run 

sudo update-grub

---

