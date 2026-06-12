---
title: "how to mount other partitions with read/write permisions?"
date: 2006-02-10
forum: Desktop Environments
---

### Post by ah.heng on 2006-02-10
i have ubuntu installed on an ATA drive.
on a seperate SATA harddisk, i made 2 ext3 partitions.

i mounted them using

```
sudo mount /dev/sda6 /mnt/sherry
```

but when i go into it using the file browser, i don't have permisions to do anything at all. can't create nor copy files.

then i tried auto-mounting it. i put this line in my fstab. but i still don't have any permisions to it.

```
/devsda6 /mnt/sherry ext3 uid=1000,umask=000 0 1
```

i remembered linking this partition to /home during installation, but it wasn't linked.

---

### Post by aysiu on 2006-02-10
Do this exactly in this order: ```
sudo umount /mnt/sherry
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` Change the line from this ```
/devsda6 /mnt/sherry ext3 uid=1000,umask=000 0 1
``` to this ```
/devsda6 /mnt/sherry ext3 defaults
``` Then save the file and close it. ```
sudo mount -a
sudo chown -R ahheng:ahheng /mnt/sherry
```

P.S. This assumes, of course, that your username is ahheng. Change it to whatever's appropriate.

---

### Post by ah.heng on 2006-02-11
worked. thanks.

---

