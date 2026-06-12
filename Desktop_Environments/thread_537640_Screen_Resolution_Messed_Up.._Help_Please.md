---
title: "Screen Resolution Messed Up.. Help Please"
date: 2007-08-29
forum: Desktop Environments
---

### Post by Pioneer5000 on 2007-08-29
Somethings wrong logged on and everything is real big the screen resolution is all messed up but when i go into system>prefrences to change screen resolution the button just screws up and doesnt let me change it. Help Please.

---

### Post by tzulberti on 2007-09-02
Open Terminal, and run "sudo dpkg-reconfigure xserver-xorg". Check taht you are using the right video driver. Near the end, it would ask you for you monitor resolution. After change it, close all the programms and run "sudo /etc/init.d/gdm restart", and it should appera in the correct resolution.

---

