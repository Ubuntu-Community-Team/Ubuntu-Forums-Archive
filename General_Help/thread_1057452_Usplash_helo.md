---
title: "Usplash helo"
date: 2009-02-01
forum: General Help
---

### Post by kangaroo738 on 2009-02-01
I'm seeing my preview then after I get this.
 
default@default-laptop:~$ sudo usplash -c
usplash: can't get console font: Invalid argument

and when I boot no image displays its says not resume image selected

---

### Post by kangaroo738 on 2009-02-01
I solved the problem for reference here it is ..

In the terminal I ran

sudo gedit /boot/grub/menu.lst

Then after my current kernel I added splash locale=en_EN vga=791

This sets the usplash to 1024 x 768. When I opened the usplash config file and manually set my resolution it wasn't enough. I needed to do this extra step.

---

