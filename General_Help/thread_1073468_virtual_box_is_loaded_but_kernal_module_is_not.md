---
title: "virtual box is loaded but kernal module is not"
date: 2009-02-18
forum: General Help
---

### Post by unix1adm on 2009-02-18
I can start virtual box fine created a winxp machine go to start it so i can load hte os and get a pop up screen telling me to run 
/etc/init.d/vboxdrv setup 

So I do and i get the following: 

root@cj454-lt:/boot/grub# /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
root@cj454-lt:/boot/grub# /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                                    
 * No suitable module for running kernel found.
root@cj454-lt:/boot/grub# /etc/init.d/vboxdrv setup
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
root@cj454-lt:/boot/grub# /etc/init.d/vboxdrv status
 * VirtualBox kernel module is not loaded.

It also tells me to load the DKMS module. well I looked in the add remove programs and there is no such file...

---

### Post by unix1adm on 2009-02-18
I found this I am guessing this is what they are talking about...


[http://linux.dell.com/projects.shtml](http://linux.dell.com/projects.shtml)

---

### Post by Therion on 2009-02-18
You may be missing some packages the VirtualBox needs.  Try installing the following packages and see if it helps.  Hooray for Cut and Paste!```
apt-get install bcc iasl xsltproc xalan libxalan110-dev uuid-dev zlib1g-dev libidl-dev libsdl1.2-dev libxcursor-dev libqt3-headers libqt3-mt-dev libasound2-dev libstdc++5 linux-headers-`uname -r` build-essential
```

---

### Post by unix1adm on 2009-02-18
i installed  and remove the vb then reinstalled the vb but get the same error as before

---

### Post by unix1adm on 2009-02-18
i may have figured this out.... 

found this and it seems to be working

[http://ubuntuforums.org/showthread.php?p=5200687](http://ubuntuforums.org/showthread.php?p=5200687)

---

### Post by unix1adm on 2009-02-18
i have a new issue now. the screen wont capture the mouse for some reason it says it is and tab works but not the mouse...

i guess back to google

---

### Post by unix1adm on 2009-02-18
ah neve rmind i have way to many computers and i was using the wrong device.

---

