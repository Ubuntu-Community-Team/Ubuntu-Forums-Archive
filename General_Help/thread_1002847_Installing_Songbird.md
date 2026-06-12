---
title: "Installing Songbird"
date: 2008-12-05
forum: General Help
---

### Post by setsanto on 2008-12-05
Hi, 
I tried to install Songbird on ubuntu 8.04.  I downloaded a .deb file for it since i wasn't sure how to handle the .xpi.  When I installed it through terminal, a whole host of errors showed up (many seemed to be related to my Dust theme).  Now it shows up as a menu item under applications, but doesn't work.  When I click on it, a message pops up saying: "Could not launch menu item.  Failed to execute child process.  (No such file or directory)  Also, the installer thinks that songbird is already installed, so I cannot reinstall, and apt-get remove Songbird has no effect.  Any advice?  All I really want to know is how to remove it.

---

### Post by aysiu on 2008-12-05
Can you paste these commands into the terminal and then post the output back here? ```
cat /etc/lsb-release
uname -m
dpkg -s songbird
sudo apt-get update
sudo apt-get remove songbird
```

---

