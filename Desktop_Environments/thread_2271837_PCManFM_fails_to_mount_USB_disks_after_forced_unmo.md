---
title: "PCManFM fails to mount USB disks after forced unmount"
date: 2015-04-02
forum: Desktop Environments
---

### Post by jeanj on 2015-04-02
Last night I forced unmount of a USB drive. 
Today I plug in the two drives I was working with, and nothing happens.
I can see them in `/dev/sd...` but they aren't being mounted.

I launched 
gnome-disks (1)      - the GNOME Disks application
and this could see the disks. 

I mounted the one successfully from gnome-disks. After this, the PCManFM mount dialog appeared.
The other disk is encrypted. When I try to unlock it, I'm told that the `luks-...` key already exists, and I can see it under `/dev/mapper/luks-...`

---

