---
title: "doesnt recognize external fat32 hdd"
date: 2008-10-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aonaran on 2008-10-06
hey, whats up guys,
thought id see if the gods of ubuntu would throw some love my way.

my problem - ubuntu wont recognize my external hard drive

my laptop - dell d610, 2.0ghz intel cpu, 60g ext3 hdd (internal), 250g fat32 hdd (external)

sudo fdisk -l returns:
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9bfa9bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7296    58605088+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc205c205

   Device Boot      Start         End      Blocks   Id  System
/BLANK

---
ive tried downloading ntfs-config and appending
/dev/hdax /mnt/sdb vfat umask=0222,dmask=0000,uid=0002,gid=users,users 0 0

to the end of it, but this did not work.

i also tried mounting the drive from the console with
sudo mkdir /media/mybook
sudo mount -t vfat /dev/sdb /media/mybook

any ideas? thanks everyone.

---

