---
title: "Mounting NTFS partition in Kubuntu"
date: 2011-04-18
forum: Desktop Environments
---

### Post by jcolyn on 2011-04-18
I am attempting to mount a Windoze 7 ntfs partition in Kubuntu.

My method so far is ```
sudo mkdir -p /media/c
```then

```
sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda1 /media/c
```This works fine till I reboot. Upon restart the drive has unmounted and I have to reenter 

```
sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda1 /media/c
``` in order to mount the drive again.

Is there a way to make it automatically mount at startup?

---

### Post by jcolyn on 2011-04-18
Got it working..

I had to install ntfs-config.

---

