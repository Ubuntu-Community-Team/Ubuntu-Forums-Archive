---
title: "need help with terminal"
date: 2006-08-12
forum: Desktop Environments
---

### Post by ksn linux on 2006-08-12
I have recently installed Ubuntu and the resolution is stuck on 640x480.  I have gone to system > preferences > Screen Resolution and the only one listed is 640x480.  I have seen on several other forums that if you open an editor in the terminal you can manually adjust the resolutions shown by typing /etc/X11/xorg.conf into the terminal, the problem is I don't know how to open the editor in the first place.  When I tried typing the command into the terminal without first opening an editor I simply got a bank page.  If sombody could post a guide it would be MOST usefull. 

please help

---

### Post by njzillest on 2006-08-12
use gedit then the directory

example 
gedit /etc/source.lst

---

### Post by stop_that on 2006-08-12
you might need to install driver for your graphics card like ATI ect.look into your graphics developers website to find lates linux drivers:rolleyes:

---

### Post by catlett on 2006-08-12
```
sudo gedit /etc/X11/xorg.conf
```
FYI...sudo invokes root priveleges so the document can be changed and not just viewed, gedit is the name of the editor you are going to use and /etc/X11/xorg.conf is the path to the document i.e. file xorg.conf in the folder X11 which is a sub-folder of etc

To run the x server configuration, enter ```
sudo dpkg-reconfigure xserver-xorg
``` This will yake you through numerous windows where you will enter the make and specifications of yur monitor, video card, mouse, keyboard etc. It is best to search for the specs on your video card and monitor before you run it. The more info you have the better the results.

Plus, as mentioned if you have an ATI or nvidia card, installing the drivers for from the make r will give you a better choice of resolutions etc. There are quite a few HOW TOs on the forum for the drivers

---

### Post by ksn linux on 2006-08-12
thank you, I have just downloaded the latest ati linux drivers and when i try to run the executable it says that i have to be the super user.  How do I do this

i just tried to use the command "sudo gedit /etc/x11/xorg.conf" and again, blank screen did i do something wrong

---

### Post by catlett on 2006-08-12
Are you tyoing a capital X for X11. Try this, enter in the terminal ```
gksudo nautilus
``` When the file browser opens you will be root and you can open the document by double-clicking. Now go to the window panel and select Computer<Filesystem<etc and scroll down to the file xorg.conf. Double click and check the document. Is it blank?

---

