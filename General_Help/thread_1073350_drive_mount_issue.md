---
title: "drive mount issue"
date: 2009-02-18
forum: General Help
---

### Post by RWise on 2009-02-18
I just installed Ubuntu 7.10 on my gals laptop, all went well except the partitioner would not let me use the whole drive so I have 3 partitions, an ext2, ext3, and a swap partition. She chose a user name and password during the install, now that it is installed I cannot mount the ext3 partition, I get denied, no permission,,,, I would like to get the partition mounted and keep it mounted for her to use as storage. I know I am overlooking something,,,,

---

### Post by blazemore on 2009-02-18
Please type ```
sudo cat /etc/fstab
``` into the terminal and paste the output here.

Also, under which folder would you like to mount the drive?

---

### Post by RWise on 2009-02-18
I had to enter her password to get this!

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=fea999f4-76d7-4c8b-8142-4988bbf42329 /               ext2    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=b9782699-e4e4-4a3a-9402-45457a8deb7e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

---

### Post by fuzzyk.k on 2009-02-18
did you choose a mount point for the ext3 drive? it doesn't seem to be in the fstab

---

### Post by RWise on 2009-02-18
most likely not, I thought (painful as it was) I did everything needed. How do I fix it? 
PS I will have to leave in a few minutes fer werk,,,,, crap,,,,

---

### Post by drs305 on 2009-02-18
Make a mountpoint (example uses *her.mountpoint*, substitute what you want in each line
```
sudo mkdir /media/her.mountpoint
```
Make her the owner:
```
sudo chown -R *her.username:* /media/her.mountpoint 
```
Example:  sudo chown -R mary: /media/mydata

Get the UUID:
```
sudo blkid -c /dev/null
```
Backup fstab and edit:
```

cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
```
Add an entry and save:
```

UUID=*uuid.obtained.from.command* /media/her.mountpoint ext3 defaults 0 2

```
Example:  UUID=UUID=3d2956b1-9f17-434b-81e9-dae7393c56e8 /media/mydata ext3 defaults 0 2

---

