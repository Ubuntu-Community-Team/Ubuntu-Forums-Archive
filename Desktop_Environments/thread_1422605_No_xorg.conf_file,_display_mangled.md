---
title: "No xorg.conf file, display mangled"
date: 2010-03-05
forum: Desktop Environments
---

### Post by feliscatus on 2010-03-05
Hi,

I am aware that there is a problem with Radeon video drivers in Karmic Koala, but most of the solutions require you to modify your xorg.conf file...but I don't have an xorg.conf file. 

```
sudo more /etc/X11/xorg.conf
/etc/X11/xorg.conf: No such file or directory
```

```
Xorg -configure

Fatal server error:
Cannot move old log file ("/var/log/Xorg.0.log" to "/var/log/Xorg.0.log.old"


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log
```

Can anyone help? 

Thanks.

---

### Post by thunk77 on 2010-03-05
You can always reconfigure your x with the command

```
sudo dpkg-reconfigure xserver-xorg
```

and follow the instructions on the screen so as to start a new

---

### Post by Flareside on 2010-03-05
X stopped using configuration files about a year ago I think and now it (is supposed to) autoconfigure itself, although sometimes it is necesary to create a config file.

---

