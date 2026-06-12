---
title: "Ati"
date: 2005-06-16
forum: Desktop Environments
---

### Post by trojan646 on 2005-06-16
win i try to install the ati driver it says 

root@ubuntu:/home/justin # sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xorg-driver-fglrx
root@ubuntu:/home/justin #


help?

---

### Post by Hokputooy on 2005-06-16
Thats becuase the driver name is just "fglrx" not "xorg-driver-fglrx". Try typing sudo apt-get install fglrx.

---

### Post by Hokputooy on 2005-06-16
Wait scratch that, That was for warty.

---

### Post by trojan646 on 2005-06-16
root@ubuntu:/home/justin # apt-get install fglrx
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package fglrx
root@ubuntu:/home/justin #

---

### Post by Hokputooy on 2005-06-16
[QUOTE=Hokputooy]Wait scratch that, That was for warty.[/QUOTE]
 Scratch that again, this is for warty.

---

### Post by nocturn on 2005-06-17
Have you enabled the universe and restricted reposistories (see Ubuntu guide).

Using synaptic, you can do a search, or use
apt-cache search fglrx

or 
aptitude search fglrx

---

