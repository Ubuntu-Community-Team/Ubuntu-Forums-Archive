---
title: "Importing data from another distro"
date: 2006-05-19
forum: Desktop Environments
---

### Post by diw on 2006-05-19
All my work is backed up on dvd.  I can access my dvd drive for all dvds except the one that has my backed up data from another distro (xandros).  The problem is that to access the drive I apparently need root permissions.  I had this problem In fedora core but here I could log in as root to a graphical screen and then access the drive and then transfer the data to my user home folder.  At an admin console I could then use the chown command to change all permissions from root to user for all directories and subdirectories.  How can can I do a similar thing in ubuntu?

---

### Post by Sef on 2006-05-19
You can do gksudo to get a temperary root.  will end when you close it.

---

### Post by ec2 on 2006-05-19
you have to enable logging in as root from the graphical login screen. go to the gdm options, from the administration menu. Under the security tab, check a flag over the "allow logging in as a root from the gdm screen". then log out, and log in as a root user. make sure that you know the root password. under root, you can access all device, everyone knows that.

---

### Post by ec2 on 2006-05-19
you have to enable logging in as root from the graphical login screen. go to the gdm options, from the administration menu. Under the security tab, check a flag over the "allow logging in as a root from the gdm screen". then log out, and log in as a root user. make sure that you know the root password. under root, you can access all devices, everyone knows that.

---

### Post by diw on 2006-05-19
Thanks for this information.  I've used it successfully and have now got all my data in my home folder with user permissions.

---

