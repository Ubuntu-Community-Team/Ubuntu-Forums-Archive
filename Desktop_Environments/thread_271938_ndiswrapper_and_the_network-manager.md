---
title: "ndiswrapper and the network-manager"
date: 2006-10-05
forum: Desktop Environments
---

### Post by fululian on 2006-10-05
i tried to get a toshiba satellite laptop to the internet with a netgear wg111t usb wlan stick. i installed the windows driver with ndiswrapper alright, it listes the driver as "hardware present: yes". after that, i installed network-manager and put a "#" before each networking device i wanted to have managed by network-manager inside the ```
/etc/network/interfaces
```.

the problem is: i restart the box, so that the network-manager may be able to offer the various choices, but instead the driver isn't installed anymore. so i redo ndiswrapper, but then have to edit the /etc/network/interfaces again. since the network-manager stays silent, i reboot...and so forth and so forth...

does anybody know how to solve this "muenchhausen"-like twist? thanks

---

