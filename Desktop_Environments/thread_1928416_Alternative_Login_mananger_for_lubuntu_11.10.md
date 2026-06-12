---
title: "Alternative Login mananger for lubuntu 11.10"
date: 2012-02-20
forum: Desktop Environments
---

### Post by thenatobourne on 2012-02-20
hello. i hate the login screen from lubuntu because i need digit the username every time.

i can install alternative login screen like in xubuntu or ubuntu to select list of users?

---

### Post by Krytarik on 2012-02-20
> **thenatobourne said:**
> i can install alternative login screen like in xubuntu or ubuntu to select list of users?
Sure you can; I recommend using the default display manager of both Ubuntu and Xubuntu 11.10, LightDM:
```
sudo apt-get install lightdm
```Upon installation, it will let you choose between the already installed display manager, LXDM, and the newly installed LightDM; then obviously choose the latter.

Later, if you want to switch back to LXDM, or another display manager, just run commands like these to bring up the same selection dialog again (you will always get the same dialog, but the specified package must be actually installed, obviously):
```
sudo dpkg-reconfigure lightdm
sudo dpkg-reconfigure lxdm
```Regards.

---

### Post by Rodney9 on 2012-02-20
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by linuxnas on 2012-02-21
> **Krytarik said:**
> 
```
sudo dpkg-reconfigure lightdm
sudo dpkg-reconfigure lxdm
```Regards.

After installation and selection of lightdm, the login manager won't start, it just hang at some process at a text terminal (black screen).  I have to login to another terminal "ctrl+alt+F2" and do dpkg-reconfigure lxdm, let it start at lxdm

any fix?

---

