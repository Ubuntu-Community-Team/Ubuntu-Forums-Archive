---
title: "accessing other partation of ubuntu system"
date: 2009-02-24
forum: General Help
---

### Post by richardmems on 2009-02-24
Dear all

My HDD is 160 GB. During Ubuntu installation, setup half into 2 partation with each ~80 GB.

one of them is the partation where is called "System Disk" for which i am root user.

The other one called 'disk' as can be seen from GUI is there. I can access and see the files  inside in GUI. 

How can i access to that drive, for  storage and new package (big scientifica software using lapack) installation?

regards
Rich

---

### Post by taurus on 2009-02-24
To access and use the other partition, you need to mount it.  You can have it mount automatically each time you boot Ubuntu by adding an entry in /etc/fstab.  What filesystem is the other partition anyway?

Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
id
```

---

