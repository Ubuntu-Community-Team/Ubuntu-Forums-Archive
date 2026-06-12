---
title: "Problem with partimage to backup"
date: 2009-05-10
forum: General Help
---

### Post by colau on 2009-05-10
Hi,
I tried to backup the partition that has ubuntu 9.04 with ext4 filesystem but failed.
Partimage can't backup the partition that has ext4 filesystem.
It says "Could not read the 0 block of that partition" something like that.
Does anyone have any idea?

---

### Post by agurk on 2009-05-10
Partimage doesn't support ext4 (yet), their homepage recommends using [FSArchiver](www.fsarchiver.org) instead.

---

### Post by agurk on 2009-05-10
Another suggestion would be to:

1. Write zeros to empty blocks (to save space when compressing later):
```
sudo dd if=/dev/zero of=/0bits bs=20971520   # bs=20m
sudo rm /0bits
```

2. dd the whole system disk (sda) with compression to a file on a separate disk (sdb1):
```
sudo dd if=/dev/sda | gzip > /media/sdb1/system_drive_backup.img.gz
```

When you want to restore, just:
```
sudo gzip -dc /media/sdb1/system_drive_backup.img.gz | dd of=/dev/sda
```

---

### Post by colau on 2009-05-10
Many thanks for your reply.
It worked fine with fsarchiver.

---

