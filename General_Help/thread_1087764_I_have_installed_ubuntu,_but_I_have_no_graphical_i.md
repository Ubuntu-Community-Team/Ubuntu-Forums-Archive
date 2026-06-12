---
title: "I have installed ubuntu, but I have no graphical interface ?!?"
date: 2009-03-05
forum: General Help
---

### Post by fa355115 on 2009-03-05
Hi there !

I have burned the ubuntu 8.10 server (gnome), booted from the CD, and installed ubuntu in dual boot with my vista, but everything I have when it is booted is a kind of console, where I can log in with my login and PW provided during the installation process.

I have no graphical interface ...

What is wrong, here ?

P.S. : my image file is called :
ubuntu-8.10-server-i386.iso

P.S. 2 : if I need to reinstall, what do I need to do with the partitioning I did for / and swap ?
Would the nre installation procedure allow me to "reuse" the 2 partitions I created for my first installation ?
(I had selected 20 Gb for ubuntu, and the swap has been created automatically)

Many thanks !

---

### Post by konqueror7 on 2009-03-05
ubuntu server doesn't come with a desktop environment, you can install it by typing in the terminal,
```
sudo apt-get install ubuntu-desktop
``` > for GNOME
```
sudo apt-get install kubuntu-desktop
``` > for KDE
```
sudo apt-get install xubuntu-desktop
``` > for Xfce

---

### Post by avtolle on 2009-03-05
Correct; you have installed the server iso, which does not come with a GUI. Server release is command line only. You may add one, if you wish; that is up to you.

---

### Post by fa355115 on 2009-03-05
I plan to re-launch the installation of the desktop soft by booting from the cd, in order to completely get rid of the server application installed. (instead of launching the installation from the server application "prompt")

Would that be ok, and will I have the choice to choose the partition that was used for my previous install (server) ?

many thanks !

---

