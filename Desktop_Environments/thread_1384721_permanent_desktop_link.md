---
title: "permanent desktop link?"
date: 2010-01-18
forum: Desktop Environments
---

### Post by carbonbased on 2010-01-18
Shiretoko wiped off my Firefox link and each time I put a new link on the desktop it's gone when I reboot.  What do I need to do to make the icon/link permanent?

---

### Post by warfacegod on 2010-01-18
If I recall, Shiretoko was an unbranded Firefox release for 3.5. Now that Firefox 3.5 has been added to the repositories there's no need to have Shiretoko. Remove it and install Firefox. Even better use Swiftfox.

---

### Post by carbonbased on 2010-01-18
> **warfacegod said:**
> If I recall, Shiretoko was an unbranded Firefox release for 3.5. Now that Firefox 3.5 has been added to the repositories there's no need to have Shiretoko. Remove it and install Firefox. Even better use Swiftfox.

Shiretoko installed itself via the Ubuntu Update Manager, about 4 days ago. I didn't ask for it and didn't want it either.  I will say that it boots about 4 times faster than FF, and I did have the latest FF installed at the time.

Nevertheless, what about making permanent links?

---

### Post by warfacegod on 2010-01-18
I would drag and drop it from your menu. If you want to be rid of shiretoko, try:

```
sudo apt-get remove shiretoko
``` or maybe purge instead of remove.

---

### Post by carbonbased on 2010-01-18
> **warfacegod said:**
> I would drag and drop it from your menu. If you want to be rid of shiretoko, try:

```
sudo apt-get remove shiretoko
``` or maybe purge instead of remove.

Synaptic Package Manager tells me FF 3.5 is installed. Neither it nor Ubuntu Software Manager tells me that Shiretoko is installed. I already told SPM to remove and reinstall FF 3.5 thinking that that might take out Shiretoko and write FF over it. No luck.

Ubuntu poorly managed this one. There was no bloody good reason why Shiretoko should have been included in an update. Bad management.

---

### Post by carbonbased on 2010-01-18
> **warfacegod said:**
> I would drag and drop it from your menu. If you want to be rid of shiretoko, try:

```
sudo apt-get remove shiretoko
``` or maybe purge instead of remove.

root@soprano:/home/richard# sudo apt-get remove shiretoko
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package shiretoko
root@soprano:/home/richard# 

Oops.

I think it's time to master the CL

---

### Post by warfacegod on 2010-01-18
This is a real shot in the dark. Try going to Synaptic> Edit> Fix Broken Packages.

If nothing then use Synaptic to completely remove shiretoko (if it's there) and Fire fox. Then fix broken packages again. Then reinstall Firefox.

---

