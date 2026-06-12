---
title: "Cannot Open Display!!!??"
date: 2005-12-18
forum: Desktop Environments
---

### Post by pittigarru on 2005-12-18
Hello, 

      I've just finished installing Ubuntu on VMware workstation, the installation went fine but when i log in it doesn't start the gui mode because of some problems with the xorg.conf, so, in command line mode i try to edit the xorg.conf file to see what's wrong but when i type sudo gedit /etc/X11/xorg.conf i get the error:

(gedit:7303): Gtk-WARNING **: cannot open display:

Anyone has any idea why?

Thank you very much.

---

### Post by psychicdragon on 2005-12-18
You can't use gedit when you're not in X. Use nano instead to view the file.

---

### Post by Rackerz on 2005-12-18
Try typing in 'startx' in the command line. If you get errors, tell us the errors then we can probably find out what exactly is wrong with the xorg.conf.

---

### Post by pittigarru on 2005-12-18
thanks for the reply, nano works but i couldn't find anything wrong in the xorg.conf, 
if i type startx to try to load the gui mode i get this :  (i've uploaded a screenshot..)
[IMG]http://img455.imageshack.us/my.php?image=screen8xu.jpg[/IMG]

the link for the image is..
[http://img455.imageshack.us/my.php?image=screen8xu.jpg](http://img455.imageshack.us/my.php?image=screen8xu.jpg)

thanks again

---

### Post by psychicdragon on 2005-12-18
Do you have the vmware driver installed?

Try running this command:
```
sudo apt-get install xserver-xorg-driver-vmware
```
If that doesn't work, can you post a copy of your **/var/log/Xorg.0.log** and **/etc/X11/xorg.conf** files here?

---

### Post by pittigarru on 2005-12-19
thank you everyone for your responses...i found out what it was, i didn't know i had to untar and manually install the vmware tools, i did that and set up the tools, restarted the x server and now everything runs smooth.:) 

thank you again

---

