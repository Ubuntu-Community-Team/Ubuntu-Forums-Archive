---
title: "Missing desktop icon for mounted usb device"
date: 2008-07-07
forum: Desktop Environments
---

### Post by vastator on 2008-07-07
I have a problem where the desktop icon for a usb device will not now up.   I know the device is automounted as I can see the files in the /media/sdb1 directory just fine.  But, the icon never displays and when I click on the storage media icon, it does not show up there as well.  Where do I need to start looking to try and isolate the problem as to why the icons will not display?

I tried restarting the dbus but that had no affect, ivman is running since it does seem to mount the devices, just no icons are available nor does kde seem to be aware of it since it is missing from dolphin or media:/

My System:
Kubuntu 8.04
Thinkpad T61
usb storage key

---

### Post by dentaku65 on 2008-07-07
Try this:
Right click on your desktop and choose Cofigure Desktop option
Choose Behavior icon on the left
Choose Device Icons tab on the right
Check if Mouted Removable Medium is selected

---

### Post by toster13 on 2008-07-07
If you used gparted before try this

```
sudo rm /etc/hal/fdi/policy/gparted-disable-automount.fdi
```

---

### Post by panosy on 2008-11-19
THANK YOU toster13!!!!!
so easy yet so hard if you don't know it..
thanx....

---

