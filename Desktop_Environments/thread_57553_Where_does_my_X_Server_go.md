---
title: "Where does my X Server go?"
date: 2005-08-16
forum: Desktop Environments
---

### Post by joopndufus on 2005-08-16
So I'm trying to install Kubuntu on a computer I just bought.  The install seems to go alright and when I reboot, the system finishes installing.  The problem comes when I reboot the system.  Everything appears to be initializing properly, the screen blanks, and then comes back to a text login.  I tried issuing 'telinit 6' with no luck.  Any ideas?

---

### Post by joopndufus on 2005-08-17
So I've tried running 'X -configure' when I log in and I get an error message along the lines of:

"Missing output drivers.  Configuration failed."

For the record, I am running Kubuntu on:

AMD XP 2600+
ASUS A7N8X Deluxe (nforce 2 chipset)
Geforce4 Ti 4200 AGP 8x

Any help guys?  I really want to stick with Kubuntu, but I need to get this up and running pretty soon.

---

### Post by heimo on 2005-08-17
Try to reconfigure X with

 ```
sudo /etc/init.d/kdm stop
sudo dpkg-reconfigure xserver-xorg
``` 

If that doesn't help, try with vesa driver.

Starting kdm:
 ```
sudo /etc/init.d/kdm start
```

---

### Post by joopndufus on 2005-08-17
[QUOTE=heimo]Try to reconfigure X with

 ```
sudo /etc/init.d/kdm stop
sudo dpkg-reconfigure xserver-xorg
``` 

If that doesn't help, try with vesa driver.

Starting kdm:
 ```
sudo /etc/init.d/kdm start
```[/QUOTE]

the vesa driver worked.  So does this mean I need to install a new driver for my video card?  Probably an nvidia driver?

---

### Post by f1dave on 2005-08-18
Luckily, vesa works for you, so if you've got an nvidia card this may help:

[http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)

---

### Post by heimo on 2005-08-18
As f1dave suggests, installing nvidia drivers is a good idea. Vesa works, but is much slower. With correct drivers, you get hardware acceleration.

---

