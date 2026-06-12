---
title: "&quot;Chown&quot;, Operation not permitted!!"
date: 2007-05-17
forum: Desktop Environments
---

### Post by CVDpr on 2007-05-17
I cant change the owner of my fat32 hda5 to cvd.

check the pic.

---

### Post by aysiu on 2007-05-17
FAT32 can't be *chown*ed, as it's not a Linux filesystem.

It needs to be mounted in a different way.

More details here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by CVDpr on 2007-05-17
nop, i cant change owner,permission still the same


# /dev/hda5
UUID=D664-FA0B  /cvd_files    vfat   iocharset=utf8,umask=000,gid=46 0       1

---

### Post by aysiu on 2007-05-17
That's your /etc/fstab line?

I don't know if that gid=46 is good or bad, but it's not necessary, so let's get rid of it. Try this line: ```
UUID=D664-FA0B /cvd_files vfat iocharset=utf8,umask=000 0 0
``` Then remount the partition: ```
sudo unmount /dev/hda5
sudo mount -a
``` If that doesn't work, reboot your computer.

---

### Post by CVDpr on 2007-05-18
Still the same, Check my original  FSTAB
=======================================
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
         proc            /proc                proc       defaults             0       0

# /dev/hda8
UUID=5ea8bc39-0799-4d27-ac35-e9c490872ab8 /  ext3    defaults,errors=remount-ro 0   1

# /dev/hda1
UUID=EC94AA9594AA6236 /media/hda1 ntfs   defaults,nls=utf8,umask=007,gid=46 0   1

# /dev/hda5
UUID=D664-FA0B  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/hda6
UUID=428C7E088C7DF6AF /media/hda6  ntfs   defaults,nls=utf8,umask=007,gid=46 0 1

# /dev/hdb1
UUID=32C2F940C2F9093D /media/hdb1  ntfs defaults,nls=utf8,umask=007,gid=46 0  1

# /dev/hdb2
UUID=90AB-CA54  /media/hdb2     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/hda7
UUID=99b446a2-8604-43f1-ae71-5cc5d4a0b054 none       swap    sw              0       0

/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by aysiu on 2007-05-18
Still the same, even after a reboot?

Okay, without modifying the /etc/fstab again, let's try a manual mount and see if that works. If that works, we can try the /etc/fstab again. ```
sudo umount /dev/hda5
sudo mkdir /cvd_files
``` if it says the folder already exists, that's cool--just keep going ```
sudo mount -t vfat /dev/hda5 /cvd_files -o iocharset=utf8,umask=000
cd /cvd_files
ls -l
```

---

### Post by CVDpr on 2007-05-18
there is nothing in the /dev all the mounts are in the /media folder(cdrom,HDs etc..)

so it's supposed to be in the /dev?

---

### Post by CVDpr on 2007-05-18
cvd@cvd-desktop:~$ sudo mount -t vfat /dev/hda5 /cvd_files -o iocharset=utf8,umask=000
Password:
mount: special device /dev/hda5 does not exist

======================================

cvd@cvd-desktop:~$ sudo mount -t vfat /media/hda5 /cvd_files -o iocharset=utf8,umask=000
mount: /media/hda5 is not a block device

Whats happening here? i remember in ubuntu 6.06 were no problems

---

### Post by aysiu on 2007-05-18
No /dev/hda5?

Can you post the output of this command? ```
sudo fdisk -l
```

---

### Post by CVDpr on 2007-05-18
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       19457   135315495    f  W95 Ext'd (LBA)
/dev/sda5            7834       15541    61914478+   b  W95 FAT32
/dev/sda6           15542       19457    31455236+   7  HPFS/NTFS
/dev/sda7            2612        2733      979902   82  Linux swap / Solaris
/dev/sda8            2734        7833    40965718+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         391     3140676    7  HPFS/NTFS
/dev/sdb2             392         784     3156772+   b  W95 FAT32


What the is the S?

---

### Post by aysiu on 2007-05-18
Ah! Looks as if it's /dev/sda5, not /dev/hda5. Can you try substituting in *s* for *h* in the above instructions?

---

### Post by CVDpr on 2007-05-18
run the command but i still cant change owner,permissions.  Thnks anyway , this thing is not going to work.

Damn there is always something... in 6.06 i never get a connection to the internet but i chagend owners etc.. in 7.04 i have internet but i cant change owners etc..


So i reformat the drive to fat32 for nothing...

---

### Post by CVDpr on 2007-05-18
ok..

1.sudo naulitus
2. media/hda5  permissions to all options to create and delete files
finish..

the owner still the root but now i can create and deletes files!!

---

