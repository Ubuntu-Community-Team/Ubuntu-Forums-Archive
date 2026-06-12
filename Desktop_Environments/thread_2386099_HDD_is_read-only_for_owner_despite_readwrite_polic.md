---
title: "HDD is read-only for owner despite read/write policy"
date: 2018-02-28
forum: Desktop Environments
---

### Post by jamesbrown2 on 2018-02-28
Logged in as gary.
Use GParted to format a hdd to ext4.
Find hdd is unusable for gary, as Gparted requires password & assigns owner of hdd/partition to root.
Change owner to gary.
Change permissions to read/write all.
Still can not copy files from ssd or usb to hdd -> Error says that hdd is read-only (despite the properties -> permissions showing gary to be owner and policy to be read/write.
I can right-click & create a new folder on the hdd; I just can not copy things to it?
Unmount/mount drives & fiddle about:  same error.
Restart computer:  it works.

Is this expected behaviour?  Why?

---

### Post by ubname on 2018-03-01
Hi, what are you using Ubuntu? version ?
In Ubuntu there is an utility (namely Disks) to format and configure mount points and any kind of mass memory.
Is you HD an internal one? an USB?
What you need to do is use Disks: format the drive, optionally configure a mount point if it is an internal one, mount point lets say /home/gary/data
then you do:```
 sudo chown -R gary:gary /home/gary/data 
```

that's it, HTH.

---

### Post by jamesbrown2 on 2019-01-21
Is HTH "heart to heart"?

---

### Post by MartyBuntu on 2019-01-21
I believe it's "happy to help".

---

