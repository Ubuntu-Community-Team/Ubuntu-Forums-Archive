---
title: "DVD-RW drive missing from /etc/fstab"
date: 2006-06-19
forum: Desktop Environments
---

### Post by arizonagroovejet on 2006-06-19
So I've got Dapper (Kubuntu) on two machines both of which have a DVD and a DVD-RW drive in them. Both DVD drives are at hdb. On one machine the DVD-RW is at hdd and on the other it's at hdc.

On both machines only the DVD drive is mentioned in /etc/fstab.

On both machines the DVD-RW drives appear to work fine. Put a disc in and it gets mounted with a mount point dynamically created in /media. K3B sees them and can use them to burn.

But I'm curious as to why only one optical drive shows up in /etc/fstab rather than both of them. Anyone know?

---

### Post by az on 2006-06-19
[QUOTE=arizonagroovejet]
On both machines the DVD-RW drives appear to work fine. Put a disc in and it gets mounted with a mount point dynamically created in /media. K3B sees them and can use them to burn.

But I'm curious as to why only one optical drive shows up in /etc/fstab rather than both of them. Anyone know?[/QUOTE]
You installed using hdb (the dvd drives), correct?  This device is added to fstab by the installer, but the other devices are only handled by HAL and udev.  So they get mounted at boot time, but are not part of fstab.

---

### Post by arizonagroovejet on 2006-06-19
[QUOTE=azz]You installed using hdb (the dvd drives), correct?[/QUOTE]

Yep.

>  This device is added to fstab by the installer, but the other devices are only handled by HAL and udev.  So they get mounted at boot time, but are not part of fstab.

Well that explains that then. I've been using one of the machines for a couple of weeks before I noticed so it's evidently a not a problem for day to use and  if I find the need I can always add an entry for them in /etc/fstab.

Cheers.

---

