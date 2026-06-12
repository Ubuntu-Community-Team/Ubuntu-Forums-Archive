---
title: "Synaptic package manager error message and linking problem??"
date: 2006-09-16
forum: Desktop Environments
---

### Post by sketchone on 2006-09-16
I recently downloaded transport tycoon duluxe as a debian/package and installed it but the installation crashed and i had to reboot my computer

when i tried to reinstall it i keep getting this error message -

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

when i launch the terminal and run - dpkg --configure -a, it tells me i need super user status

so when i SU and enter my password it says 'authenication failed' everytime

is there something i not getting here or anything i can do because this problem is stoppng me updateing my pc or installing any software

thanks in advance

---

### Post by lamego on 2006-09-16
The proper way to run admin commands on Ubuntu is:
sudo command

On your case:
```
sudo dpkg --configure -a
```

Also read the intro guide:
[https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html](https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html)

---

