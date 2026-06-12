---
title: "Boot to command line, then start Gnome"
date: 2005-11-30
forum: Desktop Environments
---

### Post by tim.n9puz on 2005-11-30
I recently installed ubuntu 5.10 with the Gnome desktop and all works fine. However, I would like to change the configuration so that I log in at the command line and stay in text mode unless I specifically start Gnome. Then, when I "logout" from the GUI I would like to go back to text mode and not actually log out.

Which config files would I need to edit to control the boot/logon process and once I can get logged in to a text mode system what command is needed to start the Gnome GUI?

Thanks,

Tim

ps -- This is my first post BTW

---

### Post by amohanty on 2005-12-01
You have two options:

1. Install an app called sysv-rc-conf. Search the forums for it, theres a howto as to how to install it. Then at the term:
sudo sysv-rc-conf

Then in there uncheck all the 'x' infront of gdm.

OR

2. in /etc/inittab 
change line 5 from:
id:2:initdefault:
to 
id:1:initdefault:

Runlevel 1 in ubuntu does not launch GDM, it does not launch a lot fo stuff so be careful!!

TO start from the command line I think (I have only used 1.)
1. startx
OR
2. gdm

HTH
AM

---

### Post by tim.n9puz on 2005-12-08
Option 1 does what I needed. Thank you for the pointers!

Tim

---

