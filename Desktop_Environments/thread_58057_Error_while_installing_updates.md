---
title: "Error while installing updates"
date: 2005-08-18
forum: Desktop Environments
---

### Post by Adam Lee on 2005-08-18
Hi there :)
I've been working on my freshly installed Ubuntu system for the whole day.
So far everything works just great, except one thing

I have linux-image-2.6.10-5-386_2.6.10-34.3_i386.deb on my update list, but when I try to update it, it gives me following error message.

> E: /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.3_i386.deb:  trying to overwrite `/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.10-5-386

It seems it has to do something with ndiswrapper. I use wireless internet. Is that a problem?

Does anyone know how can get rid of that error?
Thank you.

---

### Post by Xian on 2005-08-18
1. Uninstall ndiswrapper-modules
2. Install/Update linux-image
3. Install ndiswrapper-modules again

You can also try the install with the --force-overwrite option
but I prefer the method above.

---

### Post by lyzer on 2005-08-19
This was bugging me for a few hours glad this resolved it I removed the ndiswrapper by just following the first steps of this [tutorial](http://ubuntuforums.org/showthread.php?t=25683&highlight=update+error)
with these instructions:```
sudo modprobe -r bcmwl5
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
``` 

Thanks for your help guys I love Ubuntu!

---

### Post by chrisod on 2005-08-19
I'm getting a slightly different error trying to install the upgrade.

> E: /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.4_i386.deb:  trying to overwrite `/lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ieee80211/ieee80211.ko', which is also in package ipw2200

I updraded the ipw2200 drivers per the instructions from these forums when I first installed Ubuntu about a month ago. I suspect that is the conflict? The upgrade has the same drivers? Any advice on how to resolve would be appreciated.

---

