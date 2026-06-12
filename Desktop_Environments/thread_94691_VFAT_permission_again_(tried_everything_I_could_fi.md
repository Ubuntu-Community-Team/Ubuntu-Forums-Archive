---
title: "VFAT permission again (tried everything I could find)"
date: 2005-11-24
forum: Desktop Environments
---

### Post by DFreeze on 2005-11-24
I searched and found a lot of problems like mine, but all the solutions given did not help in my case, which is this:

I have a 80 GB FAT drive, which I use as share between Windows, Ubuntu and Network. In Hoary I could write to it, but not with Breezy. I tried the umask=000/gid/rw/auto back to default-settings, chmod 777 and WHATNOT! I think even the Queen of England can write my HD by now, but not me...

sudo nautilus does not give me write permission

my fstab shows this (after all possible alterations):

```
/dev/hdb1       /media/hdb1     vfat    rw,users,auto,umask=000		0	0
```

and fdisk -l gives:

```
Schijf /dev/hdb: 81.9 GB, 81964302336 bytes
16 koppen, 63 sectoren/spoor, 158816 cylinders
Eenheden = cylinders van 1008 * 512 = 516096 bytes

 Apparaat Boot      Start         Einde    Blokken  Id  Systeem
/dev/hdb1               1      158802    80035798+   c  W95 FAT32 (LBA)
```

typing ls -l in /media shows:

```
drwxrwxrwx  10 root root 65536 1970-01-01 01:00 hdb1
```

Yet still, whenever I drag a file in hdb1 (sudo nautilus or not), nautilus does the 'permission denied' thing. ' Sudo mkdir' in hdb1 (just to try if I can do anything in there) gives 'read only filesystem'.

Reboots give no avail, so now I call in your help. Do any of you recognise the problem? What can I do more to get write access to the disk?

---

### Post by kaamos on 2005-11-24
This worked for me:
```
/dev/hda4       /mnt/hda4       vfat    defaults,auto,uid=1000,gid=1000 0 0
```
hope this helps.

---

### Post by aysiu on 2005-11-24
Type this in a terminal ```
sudo umount /media/hdb1
```

Then, type this in ```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
```

Replace your current line: ```
/dev/hdb1       /media/hdb1     vfat    rw,users,auto,umask=000		0	0
``` with this ```
/dev/hdb1       /media/hdb1     vfat    umask=000		0	0
``` Then, save (control-x), confirm (y), and exit (enter). To remount it ```
sudo mount -a
``` Should be good now.

---

### Post by DFreeze on 2005-11-26
Those were amongst the ones I tried. Tried them again just now, but no good... What's going on here? Can it be that it doesn't work because I'm not the owner? Typing ls -l gives:

drwxrwxrwx  10 root root 65536 1970-01-01 01:00 hdb1

So the disk belongs to root. I've tried both lines in fstab given above, but they didn't work. The funny thing is: I have another FAT32 drive to which I can copy with no problems. Both have the same fstab line, both belong to root, but this other drive I can copy files to...

Is there some other settings I can lookup which might cause the troubles? The way I see it now, the fstab isn't the problem here (since it works in the other occasion), but maybe some other config file?

---

### Post by aysiu on 2005-11-26
Please don't just look at the /etc/fstab
Follow the exact directions I gave you.
The first direction was to unmount the partition.
The new permissions won't happen unless you unmount the partition and remount it.

The first command I gave you unmounts the partition.
The last command I gave you remounts it.

---

### Post by DFreeze on 2005-11-28
I know that, but omitted to mention that I first unmounted, then changed fstab, and then remounted. Even rebooten on several occasions, just to make sure...

---

### Post by DFreeze on 2005-12-01
Haven't had much time lately, but in my spare minutes I tried everything mentioned above, and some more, but no good...

I even created a new folder in /media called BDisk and did a umount, changed fstab to mount to /media/BDisk and try again. But even when the properties in GNOME say that I'm the owner, dragging a file to it gives: 'permission denied, you are not the owner'.

What in Pete's name is going on here!

I never had a problem in Hoary with this! Just change fstab once and away I went...

---

### Post by orinjuse on 2005-12-06
I'm having the same troubles. No matter what I do, even in root, I can't write to my FAT32 partitions. I've tried all the same steps as DFreeze, but nothing seems to work.

Just if it helps, here are my details:

**df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6             9.2G  2.2G  6.6G  25% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev/sdb9             5.5G  143M  5.1G   3% /boot
/dev/sdb8             4.6G  4.3G   87M  99% /home
/dev/sda2              21G   14G  7.3G  65% /media/sda2
/dev/sda5              92G   86G  6.0G  94% /media/sda5
/dev/sdb5             129G   52G   77G  41% /media/sdb5
/dev/sda5              92G   86G  6.0G  94% /media/windows

**sudo fdisk -l**
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2677       14593    95723302+   f  W95 Ext'd (LBA)
/dev/sda2   *           1        2676    21494938+   7  HPFS/NTFS
/dev/sda5            2677       14593    95723271    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb3               1       19457   156288321    f  W95 Ext'd (LBA)
/dev/sdb5            2676       19457   134801383+   b  W95 FAT32
/dev/sdb6               1        1216     9767425+  83  Linux
/dev/sdb7            1217        1338      979933+  82  Linux swap / Solaris
/dev/sdb8            1339        1946     4883728+  83  Linux
/dev/sdb9   *        1947        2675     5855661   83  Linux

Partition table entries are not in disk order

**cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb9       /boot           ext3    defaults        0       2
/dev/sdb8       /home           ext3    defaults        0       2
/dev/sda2       /media/sda2     ntfs    defaults        0       0
/dev/sda5       /media/sda5     vfat    defaults        0       0
/dev/sdb5       /media/sdb5     vfat    defaults        0       0
/dev/sdb7       none            swap    defaults              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda5       /media/windows  vfat    noauto,user,uid=1000,gid=users   0  0


I think things are getting a bit messy in there with me messing around with my newbie skills.

---

### Post by aysiu on 2005-12-06
[QUOTE=orinjuse]
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb9       /boot           ext3    defaults        0       2
/dev/sdb8       /home           ext3    defaults        0       2
/dev/sda2       /media/sda2     ntfs    defaults        0       0
**/dev/sda5       /media/sda5     vfat    defaults        0       0**
/dev/sdb5       /media/sdb5     vfat    defaults        0       0
/dev/sdb7       none            swap    defaults              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
**/dev/sda5       /media/windows  vfat    noauto,user,uid=1000,gid=users   0  0**[/QUOTE] Do you realize that /dev/sda5 is in your /etc/fstab twice? Do you also know that part of the *defaults* is it being mounted so that only root can access it? 

Unmount the partition: [code]sudo umount /media/windows
``` Then, delete both of those lines, and put this one in ```
/dev/sdb5  /media/windows   umask=000    0   0
``` Finally ```
sudo mount -a
```

---

### Post by saultpastor on 2005-12-06
Try this:

[http://www.ubuntuforums.org/showthread.php?p=443442#post443442](http://www.ubuntuforums.org/showthread.php?p=443442#post443442)

I don't know why but I was pulling my hair out over this until I used umask=0000 instead of umask=000.  Works great now.

---

### Post by DFreeze on 2005-12-10
I'm sorry to say it doesn't. I've done exactly what you described above. After that I tried some combinations again, put gid=users,user=<my_user_name> back in in combination with your suggestion, put rw,noauto,... in it, but still nothing.

I noted something strange: if I right-click, I see "Make Folder" **not** greyed out, so nautilus knows somewhere that I'm allowed to do that. But when I click it, it says "Error: Read Only Filesystem" (translated from Dutch). 

Does anyone here have any suggestions left?

---

### Post by aysiu on 2005-12-10
[QUOTE=DFreeze]
Does anyone here have any suggestions left?[/QUOTE] Yeah, since you've tried everything else... I don't know if this'll make a difference, but it's worth a shot. ```
sudo mkdir /fat_drive
sudo umount /media/hdb1
sudo gedit /etc/fstab
``` Change the line to read this ```
/dev/hdb1  /fat_drive  vfat   umask=000   0  0
``` Save and then ```
sudo mount -a
``` Then check the directory called /fat_drive

---

### Post by DFreeze on 2005-12-10
Disappointment again. I tried your approach with a directory called 'BDisk', but no writing.

Again, checking the properties of the disk shows 777, I'm the owner, the folder belongs to group 'users', and I have the 'Make Folder' option not greyed out. But I can't do anything...

I think I'll try to install KDE on it as well and see if it's a GNOME thing. Maybe something went wrong during the install, causing a random bit to be flipped. I'm all out of options it seems...

Thanks for your help so far! Don't hesitate to post new suggestions, of course. I'll keep you posted on the progress with the KDE-route.

---

### Post by DFreeze on 2005-12-11
Well, it's not a GNOME thing either. I can't write to the disk in KDE as well. Could it be I've installed a faulty Breezy-disk (I didn't do a checksum with the ISO), and somewhere deep inside some settings-file there's an option wrong?

---

### Post by aysiu on 2005-12-11
Rather than posting the same thing twice in two different threads, why don't you just post in one thread and go on from there?

FYI: This is the other thread:
[http://www.ubuntuforums.org/showthread.php?t=98892](http://www.ubuntuforums.org/showthread.php?t=98892)

---

### Post by M3ta7h3ad on 2005-12-11
This is how I did it.

After doing:

> 
mkdir /mnt/data/


> /dev/hdc2 /mnt/data vfat auto,uid=m3ta7h3ad 0 0

Adjust the above to suit you.

Documented it a bit more on me website if your interested: [http://linux.m3-computers.com/index.php?itemid=3](http://linux.m3-computers.com/index.php?itemid=3)

As mentioned on the site, that just enables access for myself. Its a single user jobby. Hopefully thats all you need as well.

---

### Post by DFreeze on 2005-12-12
Yup, the poster above is right, my two threads on this subject overlap as of now. So from here, follow the developments in [this link.]("http://ubuntuforums.org/showthread.php?t=98892")

---

### Post by hajk on 2005-12-12
Well yes, the entry in /etc/fstab for your VFAT volume /dev/hdb1 should have the umask=0000 option -- but don't forget to ALSO change the permissions of the (dummy) entry /media/hdb1 to (say) 777 with 

       sudo chmod 777 /media/hdb1 

If you don't do that, then no matter how you try to change the permissions of any files under /media/hdb1/, you'll always get the "you are not the owner..." message. Try it, it worked for me to get rw-permission on my floppy:D

---

### Post by WelterPelter on 2006-02-14
Aysui's method worked for me. Thanks.

---

