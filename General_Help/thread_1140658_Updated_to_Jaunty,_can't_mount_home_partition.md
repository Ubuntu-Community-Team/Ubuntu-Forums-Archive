---
title: "Updated to Jaunty, can't mount /home partition"
date: 2009-04-27
forum: General Help
---

### Post by Nexusx6 on 2009-04-27
Hello,

So today I decided to install Jaunty. My root and /home directories are on different partitions of my fakeRAID 0 drive, so when I did the install I just formated over the root and went about the install -- forgetting to tell set up that sda3 was my /home directory. I forgot about this until my first login on Jaunty when suddenly all my info was missing. 

Normally, no big deal, I thought "I'll just mount it and add it to fstab", but when I tried to mount my home partition to /home this is what happend.
```
fox@aurora-project:~$ sudo mount /dev/sda3 /home
mount: unknown filesystem type 'nvidia_raid_member'

```

Now I'm not sure how to solve this. My file system on sda3 is ext3, but I'm not sure why mount thinks it's 'nvidia_raid_member'.

 Here is the result of fdisk -l
```
fox@aurora-project:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c83075a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3648    29302528+  83  Linux
/dev/sda2            3649        4014     2939895   82  Linux swap / Solaris
/dev/sda3            4015       47783   351574492+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

I would greatly appreciate any help as soon as possible that I may go about installing packages and their config files to my real home directory :(

---

### Post by Retaliation on 2009-04-27
Hmmm, not sure if this would work, but you could always try it.

```
sudo mount -t ext3 /dev/sda3 /home
```

to tell it it's an ext3 fs

---

### Post by Nexusx6 on 2009-04-27
Thanks for your fast reply :D

```
fox@aurora-project:/$ sudo mount -t ext3 /dev/sda3 /home
mount: /dev/sda3 already mounted or /home busy

```

---

### Post by mb_webguy on 2009-04-27
This doesn't necessarily relate directly to the error you're getting, but...

I'd do this from a LiveCD.  You need to delete the contents of the current home directory, then add the fstab entry to mount the partition containing the original home directory.  And it's best to do this while the partitions involved aren't mounted, and while you're not using the files and directories in question.

---

### Post by Retaliation on 2009-04-27
Wierd, it thinks its already mounted.

maybe try this?

```
sudo umount /home
```

and then try the other command again

btw, I am by no means an expert on this stuff, I just had to learn some about it because I needed it for one of my computers, so I'm just throwing stuff out there.

---

### Post by Nexusx6 on 2009-04-27
> **mb_webguy said:**
> This doesn't necessarily relate directly to the error you're getting, but...

I'd do this from a LiveCD.  You need to delete the contents of the current home directory, then add the fstab entry to mount the partition containing the original home directory.  And it's best to do this while the partitions involved aren't mounted, and while you're not using the files and directories in question.

Actually, that's a smart idea. I can't do this unfortunately :( I have to use the alternate cd install since I have a fakeRAID, so I don't have a LiveCD

---

### Post by Nexusx6 on 2009-04-27
> **Retaliation said:**
> Wierd, it thinks its already mounted.

maybe try this?

```
sudo umount /home
```

and then try the other command again

btw, I am by no means an expert on this stuff, I just had to learn some about it because I needed it for one of my computers, so I'm just throwing stuff out there.
```

fox@aurora-project:/$ sudo umount /home
umount: /home: not mounted
fox@aurora-project:/$ sudo umount /dev/sda3
umount: /dev/sda3: not mounted
```

---

### Post by linuxvacuum on 2009-04-27
Since it's on a RAID array, how can it be on only 1 partition ? Shouldn't /dev/sda3 work with /dev/sdb3 or something similar? Where is the mdadm command? When I had a RAID array, I mounted /dev/md0 which was a virtual device that included 2 partitions.

---

### Post by Nexusx6 on 2009-04-27
> **linuxvacuum said:**
> Since it's on a RAID array, how can it be on only 1 partition ? Shouldn't /dev/sda3 work with /dev/sdb3 or something similar? Where is the mdadm command? When I had a RAID array, I mounted /dev/md0 which was a virtual device that included 2 partitions.

I'm not sure when you had a raid array, but I've never had to use mdadm or use a virtual device. It might be because you had an actual array vs my fakeRAID. I use dmraid raid to tinker with my array though.

---

### Post by GolemdX on 2009-04-27
Have you tried mounting to a place besides /home such as /oldhome or something and migrating it to the new partition?

---

### Post by reality1011 on 2009-04-27
> **GolemdX said:**
> Have you tried mounting to a place besides /home such as /oldhome or something and migrating it to the new partition?

This is exactly what I would do.   If I remember correctly you should log in rm -rf /home; mkdir /home then modify your fstab directory to mount the device into /home.

make sure you have at least 1 terminal open at all times, otherwise you could hose yourself.  

Btw ... here is a copy of my fstab ( I created a remote /home partition as well ) 


cappetta@Linux-Box:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=7cabe776-d82e-409b-8f53-dee811c2d77d / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=bb3bfcb3-cbb5-4071-ada2-d9de314f445d none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1       /backups        ext3    defaults,exec  0 0
**/dev/sdb2       /home           ext3    defaults,exec 0 0**
/dev/sdb3       /PROJROOT       ext3    defaults,exec 0 0

---

### Post by Nexusx6 on 2009-04-28
Much thanks for help everyone. I ended up just re-insalling since the install was fresh, I had no files on it, and it installs so fast.

@reality and GolemdX:
I like your solutions the most, and I almost did just that. If anyone runs across this post someday, I'd suggest doing what they've suggested.

---

### Post by reality1011 on 2009-04-28
> **Nexusx6 said:**
> Much thanks for help everyone. I ended up just re-insalling since the install was fresh, I had no files on it, and it installs so fast.

@reality and GolemdX:
I like your solutions the most, and I almost did just that. If anyone runs across this post someday, I'd suggest doing what they've suggested.

Thanks.  Im actually glad I posted that because I just wiped out Gutsy gibbon and installed KDE.  I need to remount my drives above and now I have the fstab


For the record, my method works as I explained...  


cappetta@kubuntu:/$  sudo mv home home1
cappetta@kubuntu:/$ sudo mkdir /home        
cappetta@kubuntu:/$ sudo vi /etc/fstab
**[COLOR="Red"]cappetta@kubuntu:/$ mount[/COLOR]**
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)

cappetta@kubuntu:/$ sudo mount /home
cappetta@kubuntu:/$ ls /home
cappetta
cappetta@kubuntu:/$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
**[COLOR="Red"]/dev/sdb2 on /home type ext3 (rw)[/COLOR]**
cappetta@kubuntu:/$

---

