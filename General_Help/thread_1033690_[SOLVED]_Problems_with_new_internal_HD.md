---
title: "[SOLVED] Problems with new internal HD"
date: 2009-01-07
forum: General Help
---

### Post by kkelly on 2009-01-07
Hi guys!

I followed some guides to mounting my hard drive and its gone quite wrong :)

I can see it just not access it in anyway

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1af6d08d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe67fe67f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sdc: 4059 MB, 4059561984 bytes
255 heads, 63 sectors/track, 493 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         493     3959991    b  W95 FAT32
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6072ab98-14e5-4f55-b26b-6fba5b6449b6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=3b9a2cfa-8ec9-4f85-b970-c57bad90a79d none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb /mnt/NTFS ntfs-3g quiet,defaults,umask=000 0 0

# /dev/sdb1

UUID=c097c2db-a71a-4965-b627-379a2c7dad8d /media/Linuxstore       ext3 auto,utf8,umask=007,uid=kevin,gid=kevin 0       0
```

---

### Post by phisher1 on 2009-01-07
Have you tried just mount -t ext3 /dev/sdb1 /media/Linuxstore to see if the partition will mount at all?

---

### Post by kkelly on 2009-01-07
Thanks for the reply:)

Not really sure how to mount hd's in Linux using guides anyway output of your command below;

kevin@kevin-desktop:~$ sudo mount -t ext3 /dev/sdb1 /media/Linuxstore
mount: mount point /media/Linuxstore does not exist

---

### Post by phisher1 on 2009-01-07
You are telling linux to mount /dev/sdb1 to a directory..
That directory has to exist..

If you want it mounted to /media/Linuxstore, and /media/Linuxstore does not exist,

sudo mkdir /media/Linuxstore

---

### Post by kkelly on 2009-01-07
Thanks phisher1,

Will I have to reboot before I am able to access the drive as it still doesn't 'work'

---

### Post by adamlau on 2009-01-07
```
sudo mkdir /media/Linuxstore
chown kevin /media/Linuxstore
```

---

### Post by kkelly on 2009-01-07
Hi Adamlau

That command didn't work :( It ran with no error but nothing happened other than I right click the hd now but still not access it

---

### Post by phisher1 on 2009-01-07
The sudo mkdir shouldn't output anything.
The chown should have errored unless ran as root.
Can you access /media/Linuxstore ?

---

### Post by kkelly on 2009-01-07
kevin@kevin-desktop:~$ cd /media/Linuxstore
kevin@kevin-desktop:/media/Linuxstore$

But when I go to Places and click on the volume i get unable to mount volume (You dont have permissions)

---

### Post by phisher1 on 2009-01-07
Ok.. 
type:

cd <enter>
sudo mount -t ext3 /dev/sdb1 /media/Linuxstore <enter>
ls /media/Linuxstore <enter>

---

### Post by kkelly on 2009-01-07
Thanks phisher1!!!

I can see it now :), will I need to edit fstab again ?

---

### Post by phisher1 on 2009-01-07
A simple fstab entry for your new drive:

/dev/sdb1 /media/Linuxstore ext3 defaults 1 2

---

### Post by kkelly on 2009-01-07
Hi 

Still got problems :(!

I rebooted and now the disk appears on my desktop? I can see the disk but not write to it still!:(

---

### Post by phisher1 on 2009-01-07
sudo chown kevin:kevin /media/Linuxstore

that is if "kevin" is your username

---

### Post by kkelly on 2009-01-07
Thanks fixed !:)

---

### Post by kkelly on 2009-01-07
Hi there,

As i have mounted this via 'media' can someone please tell me how to mount it via 'mnt' so it will not appear on my desktop ?:( don't want to break it now it works :)

Thanks Kevin.

---

### Post by phisher1 on 2009-01-07
> **kkelly said:**
> Hi there,

As i have mounted this via 'media' can someone please tell me how to mount it via 'mnt' so it will not appear on my desktop ?:( don't want to break it now it works :)

Thanks Kevin.

I would think that would be obvious..

Change everything you've done so far from media to mnt

That includes the mkdir, the chown, the fstab entry..

---

