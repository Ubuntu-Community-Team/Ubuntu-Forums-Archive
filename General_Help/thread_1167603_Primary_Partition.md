---
title: "Primary Partition"
date: 2009-05-23
forum: General Help
---

### Post by sudoomar on 2009-05-23
Hello

i am new to Ubuntu...i decided to get rid of windows and every thing related..

now i have a 260 GB hard drive

during Ubuntu 8.10 installation i made my HD like this:
first partition : 124 GB ext2 file system , mount point / ,(primary)
second partition : 124 GB ext2 file system , mount point /Storage (primary)
third partition : 2GB swap 

well Ubuntu is working fine but i am not able to create/change any files inside Storage Folder..though i am able to accesse it

please help

---

### Post by x33a on 2009-05-23
post the output of 
```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by sudoomar on 2009-05-23
it give me the following :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=06a4082c-f0f6-4488-ac42-9718e0d04f88 /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=217af2e7-e5f0-49d3-a621-66eb2b44bf45 /storage        ext2    relatime        0       2
# /dev/sda6
UUID=7bae1de2-6ce9-4e08-a940-ae66d6ef86b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by x33a on 2009-05-23
post the output of 
```
sudo fdisk -l
```

and 
```
ls -l /storage
```

---

### Post by sudoomar on 2009-05-23
1-

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99f399f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15090   121208832   83  Linux
/dev/sda2           15091       30401   122985607+   5  Extended
/dev/sda5           15091       30158   121033678+  83  Linux
/dev/sda6           30159       30401     1951866   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e6f87a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)

---

### Post by sudoomar on 2009-05-23
2-

total 48
drwxr-xr-x 2 root root 49152 2009-05-23 01:59 lost+found

---

### Post by x33a on 2009-05-23
try
```
sudo chown user:user /storage
```

where "user"= your username.

---

### Post by sudoomar on 2009-05-23
it says invalid user

omar@omar-laptop:~$ sudo chown user:omar /Storage
[sudo] password for omar: 
chown: invalid user: `user:omar'
omar@omar-laptop:~$ sudo chown user:omar /storage
chown: invalid user: `user:omar'
omar@omar-laptop:~$

---

### Post by plucky on 2009-05-23
> **sudoomar said:**
> it says invalid user

omar@omar-laptop:~$ sudo chown user:omar /Storage
[sudo] password for omar: 
chown: invalid user: `user:omar'
omar@omar-laptop:~$ sudo chown user:omar /storage
chown: invalid user: `user:omar'
omar@omar-laptop:~$


Change the command to ```
sudo chown omar:omar /storage
```

Good Luck

---

### Post by sudoomar on 2009-05-23
that works

thankx so much for help

but what does the command chown exactly do?

---

### Post by raymondh on 2009-05-23
> **sudoomar said:**
> 

but what does the command chown exactly do?

Hello,

The chown command changes user or group ownership for each given file.  In this example, the ownership (hence ability to use/read/write) was changed to omar.....pre-supposing that omar already has the necessary permissions.

Hope it helps.

Regards,

---

### Post by sudoomar on 2009-05-23
> **raymondhenson said:**
> Hello,

The chown command changes user or group ownership for each given file.  In this example, the ownership (hence ability to use/read/write) was changed to omar.....pre-supposing that omar already has the necessary permissions.

Hope it helps.

Regards,

oh thanx very much

---

### Post by x33a on 2009-05-23
previously the owner was root, with chown we changed it to omar.

since previously the owner was root, you could still do read/write operations on that partition, but only as the root user, i.e., using sudo or su.

---

