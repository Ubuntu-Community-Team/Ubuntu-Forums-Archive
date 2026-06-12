---
title: "Forcedeth drivers"
date: 2006-07-08
forum: Desktop Environments
---

### Post by That Guy X on 2006-07-08
Hi ive recintly learnd that my internet will not work on ubuntu unless i download the forcedeth driver. Does anyone know were i can get it , wich one i need and how to install it? :confused:

---

### Post by croak77 on 2006-07-09
Forcedeth is included in the default kernel. I'm using it right now. You can check to see if the module is loaded by opening a terminal and typing 'lsmod'. If you don't see it listed type 'sudo modprobe forcedeth' to load it.

---

