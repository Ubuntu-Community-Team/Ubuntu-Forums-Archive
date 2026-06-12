---
title: "Hardy AFTER Installation Problem for XPS m1530 Dell"
date: 2008-10-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zubu on 2008-10-11
mine is a XPS m1530 laptop.
I installed ubuntu 8.04.1 LTS Desktop Edition on it through the cd i had ordered from canonical.
the installation was fine.
i restarted the system after the installation was done.
after restarting i downloaded the necessary updates.
after this was done, i installed the restricted hardware driver for my nvidia 8400m GS card(nvidia-glx-new)
It asked for me to restart the system and so i did.
But this time after ubuntu was loading (i.e. the phase just before the login screen which i cant see anyways) i get an uunusual output on my screen. it has horizontal black lines (like barcodes) and some other colored lines as well!
As such i dont get to see the login screen.:(
So i have to power off my laptop to switch it off.
when i select the recovery mode option from grub for hardy and then after all the  processing i do the  " xfix " and then resume normal boot hardy starts runnig and shows me the login screen as well.everything is fine thereafter
Now, what should i do to get a normal boot .

Xps m1530
VISTA
2gb RAM
160 Gb HDD
1.6Ghz processor
nvidia 128mb 8400m GS
INDIA

UPDATES:

8.04.1 is running properly after uninstalling the nvidia-glx-new driver
but how can i install a suitable ddriver for my nvidia graphics card so that i am able to run compiz fusion?


zubair assad

---

### Post by H4ck3rz on 2008-10-16
try using envyng to install the driver 

in the synpatic packet manager search for envyng-core
& envyng-gtk i use this i dnt think it is supported but worth a try

---

