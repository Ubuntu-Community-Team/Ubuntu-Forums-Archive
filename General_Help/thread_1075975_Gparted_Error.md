---
title: "Gparted Error"
date: 2009-02-20
forum: General Help
---

### Post by krnekhelesh on 2009-02-20
I recently bought a portable external hard disk. It came with fat32 file system. I converted it into ext3 using the gparted tool.

After formatting it into ext3, I unmounted and then mounted it back...But I'm not able to create any folder, or basically write to this drive. I looked at gparted and it shows the following error message

```
Warning
Unable to find mountpoint

Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.
```

I've attached a screenshot, please help me....

---

### Post by taurus on 2009-02-20
The reason you cannot write to it because root is the owner of that mount point.  So, you need to change the ownership of the mount point for /dev/sdb1 from root to your login name.  _Assuming_ it is mounted to /media/sdb1 and your login name is lesh, you would change the ownership from a terminal with

Applications -> Accessories -> Terminal
```
sudo chown -R lesh:lesh /media/sdb1
ls -la /media
```

---

### Post by krnekhelesh on 2009-02-20
My user name is nik....so I tried
```
sudo chown -R nik:nik /media/sdb1
```

But I got the error message
```
chown: cannot access `/media/sdb1': No such file or directory
```

I thought perhaps it was not sdb1 so I tried others like sdb, sdb2...still get the same error message. Is it advisable to login as root and change the permission of /media folder?

---

### Post by taurus on 2009-02-20
Have you mounted your /dev/sdb1 yet?

Post the outputs of these commands from a terminal.

```
sudo fdisk -l
df -h
```

Otherwise, try to mount it and change the ownership with

```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
sudo chown -R nik:nik /media/sdb1
df -h
```
And when you are done using it, don't just unplug it from your machine.  You need to unmount it first before you unplug it.

```
sudo umount /media/sdb1
```

---

### Post by krnekhelesh on 2009-02-20
This is the output that I get. From the output it is mounted at sdb1, but why do I get the error message?

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        9014    72356760    7  HPFS/NTFS
/dev/sda3            9015       19457    83883397+   f  W95 Ext'd (LBA)
/dev/sda5           18153       19195     8376320   82  Linux swap / Solaris
/dev/sda6           19196       19457     2104483+  dd  Unknown
/dev/sda7            9015       11625    20972794+  83  Linux
/dev/sda8           11626       18152    52428096   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 2032 MB, 2032140288 bytes
25 heads, 24 sectors/track, 6615 cylinders
Units = cylinders of 600 * 512 = 307200 bytes
Disk identifier: 0x000d9046

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              14        6616     1980416   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81314ca2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

```

---

### Post by krnekhelesh on 2009-02-20
Thanks a lot, the other commands you mentioned made it work....Though can I ask why suddenly does it ask for root permission for mounting external drives when it hasnt done before?

And it has given me this error only because I formatted it into ext3 and then tried mounting it.Why?

---

### Post by taurus on 2009-02-20
Maybe because it was automouted when you plugged it in before.  But now you have to mount it from a terminal; therefore you have to use root privilege which of course you have to enter a password before you can use sudo.

---

