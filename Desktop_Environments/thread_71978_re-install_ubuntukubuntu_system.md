---
title: "re-install ubuntu/kubuntu system"
date: 2005-10-04
forum: Desktop Environments
---

### Post by impeteperry on 2005-10-04
I installed Ubuntu and then added a lot of the the KDE stuff including the KDE desktop, kdevelop etc. as I want to use both desktops for different functions.
While having several of the desktops open, including 2 with kdevelop, one with XMMS and one with konqueror, i did a "smart" synaptic update from within the KDE desktop.The result, apparently, was screwing up the configurations of these programs such that when rebooting I get 28 0r 29 system crash messages  and other error messages when I try to open any one of them.
Now my Question:
Is there a way to re-install ubuntu leaving my data intact or should I bite the bullet and start completely over? I do have copies of my serious stuff, but not my e-mail messages, address book music files etc.
Thanks for your advice as I am very new to Ubuntu/Kubuntu.

---

### Post by aysiu on 2005-10-04
This is why people make separate /home partitions.
/home has all your settings and preferences (and emails).
If you haven't made one already, I'd consider backing up all your /home files and creating a separate /home partition.

---

### Post by dr.diesel on 2005-10-05
I apt-get installed kubuntu-desktop on Ubuntu, and system behaved a bit strange (unable to start GDM od GNOME), maybe it was made by Warty Ubuntu distro, I only changed sources.list to Hoary and installed two more packages which were needed by kubuntu-desktop. :rolleyes: 
I had /home partition separate, but I tried to reinstall Linux complete - I didn't remember some things from previous configuration, so I practised myself in console (manually set the interfaces in configuration files made changes only for ifup, ifdown scripts not for ifconfig eth0 up/down, strange) - maybe the guide to console configuration should be also here next to configuration in X, where I don't know what happened in background :cool:

---

