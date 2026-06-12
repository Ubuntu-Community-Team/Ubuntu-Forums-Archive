---
title: "Installing GDM 2.20 Karmic Koala"
date: 2009-12-27
forum: Desktop Environments
---

### Post by efleyva on 2009-12-27
Hi im new to Linux and i decided to install Ubuntu 9.10 Karmic Koala in my laptop but when i tried to customize the login page i found that the new gdm 2.28 doesn´t permit to customize it.
I found a link [http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html/comment-page-1#comment-19754](http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html/comment-page-1#comment-19754) that explain how to install the previous version of gdm 2.20 and i ran the following script;

sudo /etc/init.d/gdm stop
sudo apt-get install gdm-2.20
cd /etc/gdm 
sudo sed ’s|X11R6/||’ gdm.conf >/tmp/gdm.conf sudo mv /tmp/gdm.conf .
startx


The problem is that i have to start the system in recovery mode , if i dont start it in recovery mode the system just freeze with a black window after the first splash screen appears … can anyone help me [IMG]http://www.ubuntugeek.com/wp-includes/images/smilies/icon_sad.gif[/IMG]  
Best Regards
ELO

---

### Post by hariks0 on 2009-12-28
Please access the following post. Read up to the last post and follow the instructions.

[http://ubuntuforums.org/showthread.php?t=1356482](http://ubuntuforums.org/showthread.php?t=1356482)

---

### Post by iPosted on 2010-01-01
> **hariks0 said:**
> Please access the following post. Read up to the last post and follow the instructions.

[http://ubuntuforums.org/showthread.php?t=1356482](http://ubuntuforums.org/showthread.php?t=1356482)


This worked perfectly, thanks!

---

