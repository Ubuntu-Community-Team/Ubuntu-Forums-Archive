---
title: "Setting KDE to be default on Ubuntu"
date: 2011-08-25
forum: Desktop Environments
---

### Post by IanWood on 2011-08-25
Hi,

I am using 10.04 and started with the normal Gnome.

I since installed KDE to try it out and would like to set it as the default. 

While installing KDE it asked if I want KDE or Gnome to be default. At the time I wasn't sure I would like KDE so said Gnome. 

I would like to do this because sometime my old Gnome desktop "shows through" and I can't shutdown or reboot from the menu, only logout. 


How do I change it so that KDE is the default?

Cheers

Ian

---

### Post by ankspo71 on 2011-08-25
Hi,
It sounds like you would like to change the default display manager (login window), so open a terminal and paste the following:
```
sudo dpkg-reconfigure gdm
```
The above command will allow you to choose between GDM and KDM. Having GDM as default has been known to stop the shutdown and restart buttons from appearing in the start menu of the KDE desktop.

As far as changing the default desktop, I am not sure how to do that, but both GDM and KDM should automatically remember your last used desktop.

[http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

Hope this helps.

---

### Post by IanWood on 2011-08-26
> **ankspo71 said:**
> Hi,
It sounds like you would like to change the default display manager (login window), so open a terminal and paste the following:
```
sudo dpkg-reconfigure gdm
```


Thanks, that exactly what I wanted. 

Works much better now.

---

