---
title: "Internal ext3 drive gone mia"
date: 2009-01-09
forum: General Help
---

### Post by jamesisin on 2009-01-09
I have this 500gb drive I plan an filling with music.  It was formatted previously in fat32.

I added it to my sysmem and booted into Ubuntu 8.10.  I went to Places and chose the 500gb drive which was then mounted and an icon appeared on my desktop.  I checked the contents to ensure it was the drive I wanted to wipe and unmounted the drive.

Then I opened GParted (System --> Administration --> Partition Editor) and switched to that drive (sdc).  I deleted the fat32 partition and applied that change.  When that was done I created a new partition (ext3) and applied that change.

This took some time, of course; but when it was done I closed GParted and took a look under Places again.  Not showing up.  No big deal; I thought I just needed to reboot.

Rebooted.  Still nothing in Places.  If I look in /dev there is no longer an entry for sdc at all (sda is my OS drive and sdb is a secondary media drive of 160gb).  Running df -h or fdisk -l confirms this.

This third ext3 drive is just gone.  I have rebooted a couple of times and it's still gone.

??

(This relates to my server building project:

[http://ubuntuforums.org/showthread.php?t=1031063](http://ubuntuforums.org/showthread.php?t=1031063) )

---

### Post by taurus on 2009-01-09
Post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by jamesisin on 2009-01-09
fdisk -l

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x133a1339

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e16bcec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux
```


df -h 
([username] removed)


```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   46G   22G  68% /
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G  216K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  2.8M  1.8G   1% /dev
tmpfs                 1.8G  108K  1.8G   1% /dev/shm
lrm                   1.8G  2.0M  1.8G   1% /lib/modules/2.6.27-9-generic/volatile
/home/[username]/.Private
                       71G   46G   22G  68% /home/[username]/Private
/dev/sdb1             147G  135G  5.2G  97% /media/disk
```


blkid


```
/dev/sda1: UUID="52a4c528-3ad6-479d-8be5-268f20b7afbe" TYPE="ext3" 
/dev/sda5: UUID="1ca057d1-b6ef-4665-bd55-23df06a64f94" TYPE="swap"
```



cat /etc/fstab


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=52a4c528-3ad6-479d-8be5-268f20b7afbe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1ca057d1-b6ef-4665-bd55-23df06a64f94 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by taurus on 2009-01-09
Unplug the 500GB drive and plug it in again, USB port I assume.  Then, post the outputs of these commands.

```
sudo fdisk -l
dmesg | tail
```

---

### Post by jamesisin on 2009-01-09
No.  This drive is internal.  Hence the internal designation in my title.

Another suggestion for internals?  (I'd rather not unplug an IDE cable on a live system.  Hehe.)

---

### Post by taurus on 2009-01-09
Does the BIOS even detect that harddrive?

---

### Post by jamesisin on 2009-01-09
That harddrive was mounted and partitioned using GParted in Ubuntu prior to rebooting.  I haven't gone back into the bios to see if it has also vanished from there.  I can do that and report back.

---

### Post by jamesisin on 2009-01-09
Thanks for putting me on the right path.

I check in the bios and this ide device was listed as "off".  So I turned it on (duh) and Auto.

Then when the box booted it gave me a message about not being able to locate a device, but I ignored that with f1.  I then confirmed it was still not showing to the OS and shutdown again.

I pulled that drive and made sure it was set to cable select.  Then I pulled the CD drive and set it to cable select (it was Master).  Popped those back in with the hdd in the master position.

Everything is back on track.

---

