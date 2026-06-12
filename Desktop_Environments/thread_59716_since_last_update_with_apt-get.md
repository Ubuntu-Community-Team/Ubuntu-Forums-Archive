---
title: "since last update with apt-get"
date: 2005-08-25
forum: Desktop Environments
---

### Post by shizow on 2005-08-25
i am newbie 
i use hoary with the standard hoary kernel
and since the update a few days ago with apt-get update, which installed new linuxheaders
many things doesnt work:
i get some error codes when i boot, the boot screen looks different 
wifi doesnot work anymore, i suggest that i reinstall the wifi driver (ipw2200)
but also when the ethernet cable is plugged, i have to type sudo dhclient eth0 to get to the internet, before this was done automatically

what happened

---

### Post by shizow on 2005-08-25
[QUOTE=shizow]i am newbie 
i use hoary with the standard hoary kernel
and since the update a few days ago with apt-get update, which installed new linuxheaders
many things doesnt work:
i get some error codes when i boot, the boot screen looks different 
wifi doesnot work anymore, i suggest that i reinstall the wifi driver (ipw2200)
but also when the ethernet cable is plugged, i have to type sudo dhclient eth0 to get to the internet, before this was done automatically

what happened[/QUOTE]

ok the problem was that this update changed my entries in grub, so i loaded always a custom not working kernel

---

