---
title: "Renaming a drive label"
date: 2009-02-04
forum: General Help
---

### Post by snowveil on 2009-02-04
Hello,

I'm sure this has been asked before, but I've tried several resources all to no avail.  I have a drive that Ubuntu (8.10) sees as "GAMES" (was the old label on a windows system) and I'd like to rename it to "misc"

I've added the following line to my /etc/fstab file
/dev/sdb1       /media/misc  vfat    defaults        0 0

and also used mtools (resourced [here](https://help.ubuntu.com/community/RenameUSBDrive) and [here](http://ubuntuforums.org/showpost.php?p=6356016&postcount=9)) to rename the drive to "misc" but all I've seemed to accomplish is disallowing GAMES from being mounted without root priviledges.

Any help would be greatly appreciated.

if helpful, here are the outputs for:
/etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b0cfd046-2e08-4ce2-9a61-400494c89c00 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=84b747eb-0c1c-4518-a117-b8752b3f0d6c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /media/seagate  ext3    defaults,user        1 2
/dev/sdb1       /media/misc  vfat    defaults        0 0

```

sudo fdisk -l
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf360c6c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa36ba36b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             893        4896    32162130    c  W95 FAT32 (LBA)
/dev/sdb2   *        4897        9729    38821072+  83  Linux
/dev/sdb4               1         892     7164958+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by Partyboi2 on 2009-02-05
Have you tried booting a ubuntu live cd an going to System>Admin>Partition Editor and unmount the GAMES partition by right clicking on the GAMES partition and selecting "unmount" then right click again and select "label" and changing it to what you like. 

You may also beable to install gparted (partition editor) without having to use a live cd as long as the partition you want to work on is not in use.
```
sudo apt-get install gparted
```

---

### Post by callan79 on 2009-02-05
> **snowveil said:**
> I'm sure this has been asked before, but I've tried several resources all to no avail.  I have a drive that Ubuntu (8.10) sees as "GAMES" (was the old label on a windows system) and I'd like to rename it to "misc"


Hi snowveil,

This isn't going to solve your problem, but I just wanted to ask .. if you're not using the Windows system any more, and this machine is pure Ubuntu, perhaps this is a good opportunity to back up the data to one of your other drives, and format the 'misc' drive to ext3 instead of fat32/vfat?

As for solving your actual issue, can you explain more about how you can't mount without root? Do you mean it won't mount at all? Or it mounts but you cannot access it?

Can you mount it, then :

```

mount
ls-l /media/

```

And paste the results?

Cheers
Callan

---

### Post by jerome1232 on 2009-02-05
I'm also curious as to what the current label is set to. That tut says it doesn't work right with 8.10 but I'm running 8.10 and just changed my little usb disks label easy enough :)

```
sudo mlabel -i /dev/sdb1 -s ::
```

---

### Post by indytim on 2009-02-05
So, if you're using Linux as your primary ops and you are mounting the partition named what you want it to be via the fstab, why not just leave well enough alone?   ... Rename it (as was suggested above) when you re-format the partition.

Just a thought...

IndyTim

---

### Post by snowveil on 2009-02-05
Thanks for all of the help guys.

Was able to get the drive relabeled, turns out it took a full reboot (not just a restart of x) to do it.  I am, however, still having issues with file permissions on the drive.  (unable to mount/unmount without being root, unable to create directories)

ls -l /media/ yeilds this:

```

total 52
drwx------  2 root root  4096 2008-12-26 09:59 CANON_DC
lrwxrwxrwx  1 root root     6 2008-06-04 09:05 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-06-04 09:05 cdrom0
drwxr-xr-x  2 root root  4096 2008-06-04 09:05 cdrom1
lrwxrwxrwx  1 root root     7 2008-06-04 09:05 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2008-06-04 09:05 floppy0
drwxr-xr-x 13 root root 32768 1969-12-31 19:00 misc
drwx------  9 mike mike  4096 2009-02-05 09:44 seagate

```

seagate can be written to and such just fine, whereas misc can not.  

ls -l /dev/sd*1 yeilds this: (misc is sdb1, seagate is sda1)
```

brw-rw---- 1 root disk 8,  1 2009-02-05 07:37 /dev/sda1
brw-rw---- 1 root disk 8, 17 2009-02-05 07:37 /dev/sdb1

```

after trying to change ownership of /media/misc using
sudo chown -R mike:mike /media/misc
the output parses through all of my files with an "Operation not permitted" error for each one, eg:
```

chown: changing ownership of `/media/misc/cave story/newmachinegame/data/Stage/Weed.pxa': Operation not permitted
chown: changing ownership of `/media/misc/cave story/newmachinegame/data/Stage/Weed.pxe': Operation not permitted
chown: changing ownership of `/media/misc/cave story/newmachinegame/data/Stage/Weed.pxm': Operation not permitted

```

any ideas?

---

### Post by ssam on 2009-02-05
if you just want the partition label changed have a look at
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by jerome1232 on 2009-02-05
Misc was the fat32 drive right?

Try changing the option to this. umask=000 set's the permisions to world readable/writable, you can adjust them to whatever, for a full listing of the options check out "man mount" and search for umask (/umask enter)

```
users,exec,suid,relatime,umask=000
```

---

### Post by snowveil on 2009-02-05
> **jerome1232 said:**
> Misc was the fat32 drive right?

Try changing the option to this. umask=000 set's the permisions to world readable/writable, you can adjust them to whatever, for a full listing of the options check out "man mount" and search for umask (/umask enter)

```
users,exec,suid,relatime,umask=000
```

that did it :)

thanks again guys for all of the help

---

### Post by hachel on 2009-02-07
Hello, I have a similar problem.
I edited my fstab to mount my ntfs-partition. It is mounted in media/windows, yet it is labeled as "32.0 GB Media" in Nautilus (and on my desktop).
I recently found out that it is properly labeled "Windows" when I start Nautilus with root-privileges. Also, I can't unmount it, it tells me I have to be root to do so. "Windows is owned by root, but I figured chown would only fix it temporaily
Here is both my fstab and the output of fisdk:
```
$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb00db00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3891    31254426    7  HPFS/NTFS
/dev/sda2            3892       35501   253907325   83  Linux
/dev/sda3           35502       38670    25454992+  83  Linux
/dev/sda4           38671       38913     1951897+  82  Linux swap / Solaris 
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=711fb909-445b-4459-9e1d-bd6844c54a46 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=147e28de-08df-45fe-9ff0-933410409f12 /home           ext3    relatime        0       2
# /dev/sda4
UUID=10037b26-7a87-4596-9bb9-7b788ef36f46 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 /media/Windows ntfs-3g defaults,locale=en_US.utf8 0 0
```

```
$ ls -l /media/
total 8
lrwxrwxrwx 1 root root    6 2009-02-06 23:00 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-02-06 23:00 cdrom0
drwxrwxrwx 1 root root 4096 2009-02-06 23:50 Windows
```


thanks

---

### Post by physeetcosmo on 2009-02-08
> **hachel said:**
> Hello, I have a similar problem.
I edited my fstab to mount my ntfs-partition. It is mounted in media/windows, yet it is labeled as "32.0 GB Media" in Nautilus (and on my desktop).
I recently found out that it is properly labeled "Windows" when I start Nautilus with root-privileges. Also, I can't unmount it, it tells me I have to be root to do so. "Windows is owned by root, but I figured chown would only fix it temporaily
Here is both my fstab and the output of fisdk:
```
$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb00db00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3891    31254426    7  HPFS/NTFS
/dev/sda2            3892       35501   253907325   83  Linux
/dev/sda3           35502       38670    25454992+  83  Linux
/dev/sda4           38671       38913     1951897+  82  Linux swap / Solaris 
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=711fb909-445b-4459-9e1d-bd6844c54a46 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=147e28de-08df-45fe-9ff0-933410409f12 /home           ext3    relatime        0       2
# /dev/sda4
UUID=10037b26-7a87-4596-9bb9-7b788ef36f46 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 /media/Windows ntfs-3g defaults,locale=en_US.utf8 0 0
```

```
$ ls -l /media/
total 8
lrwxrwxrwx 1 root root    6 2009-02-06 23:00 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-02-06 23:00 cdrom0
drwxrwxrwx 1 root root 4096 2009-02-06 23:50 Windows
```


thanks

Ok you should change the ownership AND group of the disk so then you can edit it from your account. Perform the following steps, it should help:

```
$ sudo umount /dev/sda1
```
you will have to enter the root password. Then,
```
$ sudo chown *yourusername* /dev/sda1
```
```
$ sudo chgrp *yourusername* /dev/sda1
```

Now, the fact that it is showing up on your desktop is normal--external drives even when they are mounted in another folder will show up there.:)

As far as the actual label, I am still looking. The 'label' that you are seeing as root is the 'partition label' and the fact that you still see '32 GB Media' is telling me that the actual 'disk label' is still the default (Yes these are two completely separate labels).

Then, for now to remount type:
```
sudo mount /dev/sda1 /media/windows
```

I believe to change the disk label there is a line that needs to be placed in fstab. Let me check and I'll post again.

---

### Post by hachel on 2009-02-09
thanks,

I followed those steps but I still can't unmount :(

same errormessage as before

---

### Post by hachel on 2009-03-13
hi,

i unmounted the windows-drive in gparted and chose "label" from the Partition-tab.
With that I was able to change the name of the symbol on my desktop.

Still no update on the issue of being unable to unmount it

---

