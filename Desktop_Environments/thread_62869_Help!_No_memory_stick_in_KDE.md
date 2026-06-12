---
title: "Help! No memory stick in KDE"
date: 2005-09-06
forum: Desktop Environments
---

### Post by nomeat on 2005-09-06
With Gnome the memory sticks work fine but under KDE they are not detected,
but lsusb returns:
 Bus 001 Device 003: ID 1043:8006 iCreate Technologies Corp.

I have 2 lappys. The other one displays at least the USB folder but I can not read or write any data with it.
KDE took everything over from Gnome but why not the USB function?

---

### Post by Hairy_Palms on 2005-09-06
i had the same problem, it turned out kde hated my usb2 PC card,

---

### Post by mlmurray on 2005-09-06
Go into Settings -> Desktop -> Behavior (in KDE).   Go to the "Device Icons" tab and make sure that "Unmounted removable medium" and "Mounted removable medium" are checked in the list.

Also, check the "General" tab and make sure that "Show icons on desktop" is checked.

If that doesn't work, we'll take the next step.  Remember though that KDE has no effect upon whether or not a device "works" or not, it's just not giving you an easy interface to access it.

---

### Post by nomeat on 2005-09-06
mlmurry you are a genius.
The tab to show all icons was not clicked although I could see all other icons.

Was just stange that I coudn't find them under krusader either.
Now they show up as sda1.

---

### Post by mlmurray on 2005-09-08
Glad I could help!  I think the reason you couldn't see it under krusader is that it wasn't mounted yet.  When you click on the icon on the KDE desktop, KDE uses the "Hardware Abstraction Layer" to mount the device.  It will then show up (in krusader or any other file manager) under /media/sda1.

MM

---

