---
title: "cant mount my ntfs drives"
date: 2006-07-16
forum: Desktop Environments
---

### Post by osiris999 on 2006-07-16
so i have fuse and the beta driver installed. everything installed just fine. i want to be able to access my 250 gig ntfs drive. it doesnt have any kind of os on it. only video and music files. so what to i type in x-term to mount it so i can save things in unbuntu to the drive and also access the files that are already there. ive tried

 sudo ntfs-3g /dev/sdb

and get 

Error opening partition device: Device or resource busy
Failed to startup volume: Device or resource busy
Couldn't mount device '/dev/sdb': Device or resource busy
Mount failed.

so what do i type in or how do i fix this

---

### Post by Jagot on 2006-07-16
Have a look here:

[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html)

---

