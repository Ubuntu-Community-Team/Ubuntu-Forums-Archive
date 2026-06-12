---
title: "fstab and automount not compatible?"
date: 2008-12-04
forum: General Help
---

### Post by lamps06 on 2008-12-04
This seems to be an ongoing trend I have seen in other threads.  In fact I have another thread started [_here_]("http://ubuntuforums.org/showthread.php?t=821405") but I think I have discovered a clue that merits a whole new thread.

Here is the deal.  I am running Ubuntu 8.10.  I just wiped my hard drive and did a clean install a week ago.  I am using the most recent generic kernel, 2.6.27-9.  Immediately after completing the install I plugged in a USB flash drive and it automounted fine.  After that I modified my fstab to mount my two internal IDE drives I use for media on startup.  I restarted and my IDE drives mounted fine but now my USB drive will not automount.  It shows up in Nautilus but when I double click it to mount it I get the "Unable to mount location" message.  If I remove the two entries for my IDE drives from fstab then the USB drive auto mounts fine.

Does anyone know why my fstab is screwing up my USB automounting?  Below is a copy of my fstab with the IDE entries.  Thanks!

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fc1869c6-0cad-4d4c-b71a-3b26f23b5ab1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c797da93-e0fb-45b1-b703-25c2dcc930ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

######THESE ARE THE TWO ENTRIES I MADE####

# /dev/sdb1
UUID=E8909F03909ED800
/dev/sdb1	/media/Media_Drive	ntfs	defaults 0 0

# /dev/sdc1
UUID=C830453E3045352A
/dev/sdc1	/media/WinXP	ntfs	defaults	0	0

```

---

### Post by taurus on 2008-12-04
> **lamps06 said:**
> This seems to be an ongoing trend I have seen in other threads.  In fact I have another thread started [_here_]("http://ubuntuforums.org/showthread.php?t=821405") but I think I have discovered a clue that merits a whole new thread.

Here is the deal.  I am running Ubuntu 8.10.  I just wiped my hard drive and did a clean install a week ago.  I am using the most recent generic kernel, 2.6.27-9.  Immediately after completing the install I plugged in a USB flash drive and it automounted fine.  After that I modified my fstab to mount my two internal IDE drives I use for media on startup.  I restarted and my IDE drives mounted fine but now my USB drive will not automount.  It shows up in Nautilus but when I double click it to mount it I get the "Unable to mount location" message.  If I remove the two entries for my IDE drives from fstab then the USB drive auto mounts fine.

Does anyone know why my fstab is screwing up my USB automounting?  Below is a copy of my fstab with the IDE entries.  Thanks!

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fc1869c6-0cad-4d4c-b71a-3b26f23b5ab1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c797da93-e0fb-45b1-b703-25c2dcc930ff none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

######THESE ARE THE TWO ENTRIES I MADE####

[B][COLOR="Blue"]# /dev/sdb1
UUID=E8909F03909ED800
/dev/sdb1	/media/Media_Drive	ntfs	defaults 0 0

# /dev/sdc1
UUID=C830453E3045352A
/dev/sdc1	/media/WinXP	ntfs	defaults	0	0[/COLOR][/B]

```

Those two entries look weird to me.  They should look like these.

```

UUID=E8909F03909ED800   /media/Media_Drive	ntfs	defaults   0   0
UUID=C830453E3045352A   /media/WinXP	ntfs	defaults	0   0

```

---

### Post by lamps06 on 2008-12-05
You, sir, are a genius!  Your suggestion fixed my problem.  You have no idea how annoying this has been for the past eight months.  THANK YOU!

---

### Post by polka on 2009-02-08
I have been following this thread with great interest but have not commented because I did not have anything new to contribute.
I have tried all the suggestions here with no luck. 
The thread started by lamp_06 partially solved the problem [http://ubuntuforums.org/showthread.php?t=1002088](http://ubuntuforums.org/showthread.php?t=1002088)
I used the method there to fix my fstab file and now when I plug in my usb flash drive it automounts but I do not get an icon on my desktop. At least partial success.
Here is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f0c184c7-1c55-489f-81c9-4af03d486228 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=71f95d13-2d45-429c-9764-ec51ff801d40 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /home   ext3    relatime,errors=remount-ro 0    0
#/dev/sdc1      /media/temp     ext3    defaults                        0       0
#/dev/sdc       /media/temp     vfat    defaults                        0       0
#/dev/sdc1 PATRIOT usb drive
UUID=498E-FCDD  /media/PATRIOT  vfat    defaults,relatime,auto          0       0

The strange thing is that my Patriot drive is mounted on /media/sdc1.
Here is my mount command:
/dev/sdc1 on /media/sdc1 type vfat (rw,noexec,nosuid,nodev,quiet,shortname=mixed,uid=112,gid=46,umask=007,fmask=0117,dmask=0007)

I did remove flush but that did not work; only the change in fstab worked.

Thanks for you dogged persistence with this problem.
Jerry
P.S. After inspecting the situation further I have commented out the line for the patriot flash drive and it still automounts on sdc1 and has a file in /media/sdc1 (with out the flash drive mounted) :  .created_by_pmount
This is beyond my understanding.

---

### Post by fizzy77 on 2009-02-17
I have had the same problem. Since modifying my fstab to mount my two IDE drives I am unablt to auto mount USB drives. I can see them in Places etc but am unable to mount them. I'm not getting any error messages though, nothing happens.

This is my fstab:

```
# /etc/fstab: static file system information.
UUID=94b27ca5-6c92-462b-9c3a-98899daf84c5#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aeea89e1-7996-4445-97b1-09177ac89b51 /               ext3    relatime,erro$
# /dev/sda5
UUID=4cbaf01c-be57-4c19-a545-67453aa47977 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
UUID=d5fabcf5-89c6-4264-804d-cd3ebba69c5a /media/300data ext3 defaults 0 0
#
UUID=94b27ca5-6c92-462b-9c3a-98899daf84c5 /media/40backup ext3 defaults 0 
```

---

### Post by taurus on 2009-02-17
> **fizzy77 said:**
> I have had the same problem. Since modifying my fstab to mount my two IDE drives I am unablt to auto mount USB drives. I can see them in Places etc but am unable to mount them. I'm not getting any error messages though, nothing happens.

This is my fstab:

```
# /etc/fstab: static file system information.
UUID=94b27ca5-6c92-462b-9c3a-98899daf84c5#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aeea89e1-7996-4445-97b1-09177ac89b51 /               ext3    relatime,erro$
# /dev/sda5
UUID=4cbaf01c-be57-4c19-a545-67453aa47977 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
UUID=d5fabcf5-89c6-4264-804d-cd3ebba69c5a /media/300data ext3 defaults 0 0
#
UUID=94b27ca5-6c92-462b-9c3a-98899daf84c5 /media/40backup ext3 defaults 0 **[COLOR="Blue"]0[/COLOR]**
```

What are the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
df -h
ls -la /media
```

And by the way, you are missing a **0** at the end of the last entry in /etc/fstab.  And what's up with the $ at the end of a couple of entries?

---

### Post by fizzy77 on 2009-02-17
Sorry the $s where because of the size of my terminal window! and the missing 0 from hasty copy and paste. the correct fstab is below:

```
# /etc/fstab: static file system information.
UUID=94b27ca5-6c92-462b-9c3a-98899daf84c5#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aeea89e1-7996-4445-97b1-09177ac89b51 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4cbaf01c-be57-4c19-a545-67453aa47977 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
UUID=d5fabcf5-89c6-4264-804d-cd3ebba69c5a /media/300data ext3 defaults 0 0
#
UUID=94b27ca5-6c92-462b-9c3a-98899daf84c5 /media/40backup ext3 defaults 0 0

```

The output from the commands you gave are as follows:
```
dan@Dirkbuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a726f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60046   482319463+  83  Linux
/dev/sda2           60047       60801     6064537+   5  Extended
/dev/sda5           60047       60801     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f273d07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4866    39079936   83  Linux

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0545c11

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36484   293054464   83  Linux

Disk /dev/sdd: 8040 MB, 8040480256 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         976     7839698    b  W95 FAT32


dan@Dirkbuntu:~$ sudo blkid
/dev/sda1: UUID="aeea89e1-7996-4445-97b1-09177ac89b51" TYPE="ext3" 
/dev/sdb1: LABEL="40backup" UUID="94b27ca5-6c92-462b-9c3a-98899daf84c5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="d5fabcf5-89c6-4264-804d-cd3ebba69c5a" TYPE="ext3" SEC_TYPE="ext2" LABEL="300data" 
/dev/sdd1: UUID="8359-CEF3" TYPE="vfat" 
/dev/sda5: TYPE="swap" UUID="4cbaf01c-be57-4c19-a545-67453aa47977" 


dan@Dirkbuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             453G   65G  366G  15% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  344K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.9M 1009M   1% /dev
tmpfs                1012M  104K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdc1             276G  212G   50G  81% /media/300data
/dev/sdb1              37G  5.4G   30G  16% /media/40backup
/dev/scd0             103M  103M     0 100% /media/cdrom0



dan@Dirkbuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             453G   65G  366G  15% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  344K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.9M 1009M   1% /dev
tmpfs                1012M  104K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdc1             276G  212G   50G  81% /media/300data
/dev/sdb1              37G  5.4G   30G  16% /media/40backup
/dev/scd0             103M  103M     0 100% /media/cdrom0
dan@Dirkbuntu:~$ ls -la /media
total 18
drwxr-xr-x  5 root root 4096 2009-02-17 20:08 .
drwxr-xr-x 20 root root 4096 2009-02-16 19:18 ..
drwxr-xr-x  8 dan  dan  4096 2009-02-16 21:52 300data
drwxr-xr-x  5 dan  dan  4096 2009-02-16 23:46 40backup
lrwxrwxrwx  1 root root    6 2009-02-10 21:08 cdrom -> cdrom0
dr-xr-xr-x  1 root root 2048 2006-03-21 12:27 cdrom0
-rw-r--r--  1 root root    0 2009-02-17 19:55 .hal-mtab

```

Both IDE drives seem to be working perfectly (it would seem to me anyway).

---

### Post by taurus on 2009-02-17
> **fizzy77 said:**
> Sorry the $s where because of the size of my terminal window! and the missing 0 from hasty copy and paste. the correct fstab is below:

```
# /etc/fstab: static file system information.
**[COLOR="Red"]UUID=94b27ca5-6c92-462b-9c3a-98899daf84c5#[/COLOR]**
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aeea89e1-7996-4445-97b1-09177ac89b51 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4cbaf01c-be57-4c19-a545-67453aa47977 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#
UUID=d5fabcf5-89c6-4264-804d-cd3ebba69c5a /media/300data ext3 defaults 0 0
#
UUID=94b27ca5-6c92-462b-9c3a-98899daf84c5 /media/40backup ext3 defaults 0 0

```

Do you really have that line in your /etc/fstab?  Isn't that the UUID for /dev/sdb1?

---

### Post by fizzy77 on 2009-02-17
Doh! I feel a bit stupid now... I realy need to watch tha copy 'n' paste!

I only installed Ubuntu last week so it's all a bit new. I love it though, it's nice to be in control again. Even is that does mean I can screw it up.

Cheers again, all working now.

---

### Post by D_one on 2009-02-18
OK, this seems to be the best forum for my problem.  I think it started when I changed the file permissions to my internal vfat partition that holds my media and all the subsequent folders (could have been something else tho).  Basically I can no longer mount the partition.  First I got an error something like "you do not have permissions to mount" Then In root nautalus I was able to mount.  

ok, I then tried to use storage device manager to make the drive automount on start but it didnt work.  However using partition editor I was able to get the drive to mount, just right click and "mount to location".  The problem seems somehow related to a discrepency in the labeling of mount points or drive names speciffically between sda7 and sda8, one being swap, the other being the drive I wish to mount: 

Storage Device manager shows:
sda7- as swap
Sda8- as vfat

Gparted and Mount manager show the opposite: 
sda7-vfat
sda8- swap

If I use mount manager to change the drive to be mountable by any user it changes my fstab file, and after that I can mount and unmount the drive.  But that doesnt stick when I restart, fstab reverts back to it's original version, I even tried changing it and saving it.  

My Fstab on boot looks like this: 
proc                                       /proc        proc  defaults    0  0  
UUID=f4bcd6b8-8e6e-409a-9937-4cdce6acb903  /            ext3  relatime,errors=remount-ro,data=writeback,noatime 0  0  1  
UUID=e77a21ec-6d5b-4ff4-92c9-81becf7fc369  none         swap  sw          0  0  
/dev/sda2                                  /media/sda2  vfat  defaults    0  0  
/dev/sda5                                  /media/sda5  ntfs  defaults    0  0  
/dev/sda6                                  /media/sda6  ext3  defaults    0  0  
/dev/sda7                                  /media/sda7  swap  users,user  0  0  
/dev/sda8                                  /media/sda8  vfat  users,user  0  0  


After I mount the drive, with mount manager it looks like this: 

UUID=f4bcd6b8-8e6e-409a-9937-4cdce6acb903  /            ext3  relatime,errors=remount-ro,data=writeback,noatime 0  0  1  
UUID=01C9794CDBCD25A0	/media/sda5	ntfs	defaults	0	0
UUID=f4bcd6b8-8e6e-409a-9937-4cdce6acb903	/	ext3	defaults	0	0
UUID=e77a21ec-6d5b-4ff4-92c9-81becf7fc369	swap	swap	sw	0	0
UUID=4973-AEA2	/media/sda7	vfat	users	0	0


Another interesting aspect is that when it is mounted it still doesnt show the drives name, it just shows it as 87gb media instead of "Files" which is what it is labeled as.  

Fdisk -l shows: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92e4538c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3188    25607578+   7  HPFS/NTFS
/dev/sda3           19453       19457       40162+  ef  EFI (FAT-12/16/32)
/dev/sda4            3189       18431   122439397+   f  W95 Ext'd (LBA)
/dev/sda5            3189        3218      240943+   7  HPFS/NTFS
/dev/sda6   *        3219        6405    25599546   83  Linux
/dev/sda7            6406       17808    91594566    b  W95 FAT32
/dev/sda8           17809       18431     5004216   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8199 MB, 8199864320 bytes
255 heads, 63 sectors/track, 996 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000888c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         996     8000338+   b  W95 FAT32


sudo blkid:

/dev/sda1: UUID="A4EC3CCCEC3C9B0E" TYPE="ntfs" 
/dev/sda2: UUID="99a87958-e4cb-4319-989a-68c94899a661" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="01C9794CDBCD25A0" LABEL="D:" TYPE="ntfs" 
/dev/sda6: UUID="f4bcd6b8-8e6e-409a-9937-4cdce6acb903" TYPE="ext3" 
/dev/sda7: UUID="4973-AEA2" TYPE="vfat" 
/dev/sda8: TYPE="swap" UUID="e77a21ec-6d5b-4ff4-92c9-81becf7fc369" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdb1: LABEL="DYLANBACKUP" UUID="4998-D9BF" TYPE="vfat" 
/dev/sdc1: SEC_TYPE="msdos" LABEL="80GBHD" UUID="4985-BCB4" TYPE="vfat" 


df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              25G   14G  9.4G  59% /
varrun               1009M   84K 1008M   1% /var/run
udev                 1009M  2.8M 1006M   1% /dev
tmpfs                1009M   12K 1009M   1% /dev/shm
/dev/sda5             236M   65M  171M  28% /media/sda5
/dev/sda7              88G   80G  8.0G  91% /media/sda7

ls -la /media:

total 144
drwxrwxrwx  9 root root    4096 2009-02-18 11:57 .
drwxrwxrwx 20 root dylan   4096 2009-02-01 23:20 ..
lrwxrwxrwx  1 root root       6 2009-01-18 05:05 cdrom -> cdrom0
drwxrwxrwx  2 root root    4096 2009-01-18 05:05 cdrom0
-rw-r--r--  1 root root       0 2009-02-18 11:57 .hal-mtab
-rw-------  1 root root       0 2009-02-18 11:34 .hal-mtab-lock
drwxr-xr-x  2 root root    4096 2009-02-17 00:23 sda1
drwxrwxrwx  2 root root    4096 2009-01-24 20:45 sda2
drwxrwxrwx  1 root root    4096 2009-01-27 11:44 sda5
drwxrwxrwx  2 root root    4096 2009-01-24 20:45 sda6
drwxr-xr-x 12 root root  114688 1969-12-31 19:00 sda7
drwxrwxrwx  3 root root    4096 2009-02-16 20:55 sda8


Any help for this here?
Thanks in advance:)

---

### Post by D_one on 2009-02-18
Furthermore, I forgot to mention that even when I mount the partition (seems to be to sda7) it is still locked in that I can acess the files but cant edit them, all my documents are in "a read only mode".  My thesis is on there!

---

### Post by D_one on 2009-02-18
Update: I was sucessfull in changing the file permissions by unmounting the drive in root nautalus and then changing the permissions thus my new  ls -la /media: 

total 36
drwxrwxrwx  9 root root  4096 2009-02-18 11:57 .
drwxrwxrwx 20 root dylan 4096 2009-02-01 23:20 ..
lrwxrwxrwx  1 root root     6 2009-01-18 05:05 cdrom -> cdrom0
drwxrwxrwx  2 root root  4096 2009-01-18 05:05 cdrom0
-rw-r--r--  1 root root     0 2009-02-18 11:57 .hal-mtab
-rw-------  1 root root     0 2009-02-18 11:34 .hal-mtab-lock
drwxr-xr-x  2 root root  4096 2009-02-17 00:23 sda1
drwxrwxrwx  2 root root  4096 2009-01-24 20:45 sda2
drwxrwxrwx  1 root root  4096 2009-01-27 11:44 sda5
drwxrwxrwx  2 root root  4096 2009-01-24 20:45 sda6
drwxrwxrwx  2 root users 4096 2009-01-24 20:45 sda7
drwxrwxrwx  3 root root  4096 2009-02-16 20:55 sda8

---

### Post by D_one on 2009-02-18
EDIT: yet again, when I reboot, it changes my partition permissions to: 

drwxr-xr-x 12 root root  114688 1969-12-31 19:00 sda7

So Im not sure if this is a fstab identity problem since storage device mmanager and fstab still mix up sda7 and sda8 (see my first post), when compared to my outputs of:

sudo fdisk -l
sudo blkid
df -h
ls -la /media

as well as the partition editor and mount manager which all show it in sda7.  Or is this a permissions problem?

Any Ideas?

---

### Post by D_one on 2009-02-18
I guess I should have started my own thread, too many posts...lol

I solved the puzzle with the  advice from this thread: 
[http://ubuntuforums.org/archive/index.php/t-811945.html](http://ubuntuforums.org/archive/index.php/t-811945.html)

Basically the key is that You can identify partitions/drives/mount points in different ways: as Label, Name, or UUID; When editing fstab, the inconsistency arises when you use the first two because they are not static.  Identifying them by UUID in fstab resolves this.  I used Mount Manager to correctlyy identify the disks and simply cut and paste the uuid into my fstab to mount to the correct mount point!  It seems this is a bug that many others have had and has had bugs filed, its a problem that should be corrected.  I hope this can help someone else.  Im sure there is a terminal code to do the same, something like:

sudo blkid (to get the UUID, copy it to clipboard)
sudo gkedit /etc/fstab (too use uuid instead of label or name to identify disk)

As for my file permissions, a whole different story, but still the kkey was in fstab and using uid=1000 and gid=1000 instead of the terms user, users, root, etc.  which never seemed to work.  Another important point was that vfat cannot accept permission changes, it was all due to whatever i did in fstab; after a day or so of searching, I found this page:

[http://ubuntuforums.org/archive/index.php/t-217492.html](http://ubuntuforums.org/archive/index.php/t-217492.html)

it was geco's line that worked for me...finally: 

/dev/hda2 /mnt/winc vfat rw,exec,uid=1000,gid=1000,auto 0 0

It seems this should have been easier for me to find.  Wiki maybe?

---

