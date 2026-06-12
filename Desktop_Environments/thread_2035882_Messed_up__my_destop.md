---
title: "Messed up  my destop"
date: 2012-07-31
forum: Desktop Environments
---

### Post by Doodaad on 2012-07-31
I have been using kde on my Dell inspiron 1300 for some time now and I got the bright idea to remove gnome completely. I did a apt-get remove gnome* and restarted. Now i get an error that X cannot find any device drivers and gives me the option to start in low graphics mode. It gets stuck on Checking battery. Pressing alt+f2 logging in and typing startx starts KDE and all seems normal except the system runs very hot and Games freeze on load screen. 
I reinstalled Kubuntu desktop and I still have to alt f2 and startx. Is there a way to force x-11/ kde to reconfigure the display? Please let me know any info you need me to post. the graphics chip is an Intel 915GM/GSM/910GML.

Thanks

---

### Post by Doodaad on 2012-08-03
> **Doodaad said:**
> I have been using kde on my Dell inspiron 1300 for some time now and I got the bright idea to remove gnome completely. I did a apt-get remove gnome* and restarted. Now i get an error that X cannot find any device drivers and gives me the option to start in low graphics mode. It gets stuck on Checking battery. Pressing alt+f2 logging in and typing startx starts KDE and all seems normal except the system runs very hot and Games freeze on load screen. 
I reinstalled Kubuntu desktop and I still have to alt f2 and startx. Is there a way to force x-11/ kde to reconfigure the display? Please let me know any info you need me to post. the graphics chip is an Intel 915GM/GSM/910GML.

Thanks


Can anyone help me out?

---

### Post by First Taste Hooks You on 2012-08-03
So you install Ubuntu and then installed kubuntu-desktop package and now you want to remove the ubuntu/gnome parts?

If you wish to do this then, you should get a new kubuntu iso or reinstall the gnome packages and remove the ubuntu-desktop package.

---

### Post by claracc on 2012-08-04
you can try to run the grub recovery mode and fix broken packages: 

[http://ubuntugenius.wordpress.com/2011/01/25/ubuntu-not-booting-try-repairing-broken-packages-in-recovery-mode/](http://ubuntugenius.wordpress.com/2011/01/25/ubuntu-not-booting-try-repairing-broken-packages-in-recovery-mode/)

---

### Post by stanciugabriel on 2012-08-04
Or, if nothing works, there is always an reinstall.

---

### Post by Doodaad on 2012-08-11
grub recovery did not help. I am going to back up my data and reinstall. Thanks

---

