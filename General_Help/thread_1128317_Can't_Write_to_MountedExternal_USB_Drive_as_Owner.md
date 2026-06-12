---
title: "Can't Write to MountedExternal USB Drive as Owner"
date: 2009-04-17
forum: General Help
---

### Post by Pipistrelle on 2009-04-17
Hello, folk. I have a Seagate external drive, and I can mount it using the command line. I can read from it, but I can't save files to it. I tried tweaking permissions with no change. 

Thanks in advance for any help.

---

### Post by taurus on 2009-04-17
What filesystem is that external drive?

```
sudo fdisk -l
df -h
```

---

### Post by Pipistrelle on 2009-04-17
The external drive has a FAT file system.

---

### Post by taurus on 2009-04-17
Assuming it's /dev/sdb1, try

```
sudo umount /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
ls -la /media
```

---

### Post by Pipistrelle on 2009-04-18
That did it! Thanks so much! I can now back up my personal data.

---

