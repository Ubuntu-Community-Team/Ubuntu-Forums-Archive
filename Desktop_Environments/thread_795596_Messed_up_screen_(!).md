---
title: "Messed up screen (!)"
date: 2008-05-15
forum: Desktop Environments
---

### Post by d_h_benson on 2008-05-15
Hi, 


A picture is worth a thousand words, so here goes:[IMG]http://www.music.mcgill.ca/~benson/screen.png[/IMG]


I tried changing my screen resolution and ended up with this unfortunate result.  This happens after I log in; the login screen looks fine.


I'm running Ubuntu 8.04 on a virtual machine using Parallels (build 3214). The actual machine is a Macbook.


Any ideas?


Many thanks,



Dave

---

### Post by amingv on 2008-05-15
You can reset your screen to the default settings like this: Ctrl + Alt + F1 > login > type
```
sudo dpkg-reconfigure -phigh xserver-xorg
logout
```
then Ctrl + Alt + F7 > Ctrl + Alt + Backspace

---

