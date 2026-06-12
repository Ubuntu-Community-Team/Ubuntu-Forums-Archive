---
title: "Need to Mount Fat32"
date: 2007-12-10
forum: Desktop Environments
---

### Post by BFMC999 on 2007-12-10
I'm completely new to Ubuntu and I barely understand the terminal session. I have a 120GB  FAT32 disk and a 80GB with one partition for Ubuntu and one that i don't know anything about. The 2 non ubuntu partitions show up but i can't access them. The 120 has a lot of stuff i need. Any suggestions?

---

### Post by sbodas on 2007-12-11
What do you mean you can't access them?  Is your FAT32 partition mounted but you get "access denied" messages, or are they unmounted?  If you need to mount it, try doing:
```

$ sudo mount -t vfat /dev/FAT32 /mnt/FAT32

```

Adjust "FAT32" to point to the fat32 partition.

---

### Post by kpkeerthi on 2007-12-11
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

