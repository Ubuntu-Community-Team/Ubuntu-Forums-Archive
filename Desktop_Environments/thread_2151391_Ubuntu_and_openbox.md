---
title: "Ubuntu and openbox"
date: 2013-06-04
forum: Desktop Environments
---

### Post by swarrier on 2013-06-04
Openbox on Crunchbang (Debian-based) is a quick, no-nonsense interface, but lacks the wifi driver for the Realtek RTL8732ae on my Toshiba. I've got Xubuntu going on the computer, but would prefer to switch to Openbox. I assume this is possible because Openbox should run on most, if not all, linux implementations. What do I need to do to get Openbox running on Xubuntu?

Thanks in advance.

---

### Post by vasa1 on 2013-06-04
I'd think that **sudo apt-get openbox** should do it. You could first run **apt-cache show openbox** to get a little more information. At your next log-in, you should see Openbox as an option.

---

### Post by sudodus on 2013-06-04
Openbox comes with Lubuntu, and the simple Openbox window manager is already an option at the login screen of Lubuntu. (It is also used by LXDE, the desktop environment of Lubuntu).

I would support the advice by *vasa1*. Only if you have problems, for example, that some important configuration is missing, you can install lubuntu-desktop to get Openbox. (In that case you can remove packages, that came with the installation, but are not necessary for you.)

---

