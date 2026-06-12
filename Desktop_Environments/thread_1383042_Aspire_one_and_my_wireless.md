---
title: "Aspire one and my wireless"
date: 2010-01-16
forum: Desktop Environments
---

### Post by New5teve on 2010-01-16
Hi, new to linux, and loving it for the most part. The tutorial [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) helped me greatly in installing ubuntu and getting the gnome enviornment working correctly. I'm trying to get the KDE desktop set up and i don't know how to set up my wireless card. I got it working with the gnome enviornment, now was wanting to get it working with the KDE desktop enviornment as well. Any help would be appreciated.

EDIT: I should mention i had to add 'blacklist acer_wmi' to the blacklist.conf file to get it to work correctly in gnome.
Also, here are some specs on my system.
Acer aspire one AOD250
Ubuntu 9.10

---

### Post by New5teve on 2010-01-16
OK, so digging around i've found out that KDE is not recognizing that i have a wireless card installed. Gnome is seeing it fine. Any ideas?

---

### Post by k64 on 2010-01-16
Try configuring your wireless connection in GNOME, opening a terminal window, and running ```
sudo apt-get install kubuntu-desktop
```. I have an Acer Aspire One myself, and it configured fine that way.

---

