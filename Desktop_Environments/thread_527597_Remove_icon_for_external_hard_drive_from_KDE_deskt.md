---
title: "Remove icon for external hard drive from KDE desktop"
date: 2007-08-16
forum: Desktop Environments
---

### Post by srunni on 2007-08-16
Hi,

Does anyone know how to remove the icon for an external hard drive from the KDE desktop? I still want to have icons for flash drives, etc.

Thanks in advance for the help!!

---

### Post by ivesjd on 2007-08-20
The way I thought it worked is mount something in /media and it would show up on the desktop, mount it /mnt and it would not. However, this does not seem to be the case anymore. If anyone knows why, I would really like to know.

---

### Post by varonbondumb on 2008-05-25
Press ALT+F2 and in the "Run application" dialog type the following command then click "Run".

gconf-editor

Then navigate on the left to Apps --> Nautilus --> Desktop and you will find an option called "volumes_visible". Switch that off. You'll note the change will take effect immediately. You can try toggling it on and off to show it working.

(found from [https://answers.launchpad.net/ubuntu/+question/2625](https://answers.launchpad.net/ubuntu/+question/2625) )

---

