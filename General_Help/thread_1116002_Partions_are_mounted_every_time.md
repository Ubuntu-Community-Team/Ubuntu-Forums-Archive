---
title: "Partions are mounted every time?"
date: 2009-04-04
forum: General Help
---

### Post by soomro on 2009-04-04
when ever i restart my computer the partitions are mounted each time is there any way so they are mounted only for once and all?

---

### Post by cariboo on 2009-04-04
That is normal operation. All operating systems mount the partitions every time you boot.

Jim

---

### Post by jigsaws on 2009-04-04
What partitions?
You can specify what should be auto mounted in /etc/fstab file.

---

### Post by soomro on 2009-04-04
> **cariboo907 said:**
> That is normal operation. All operating systems mount the partitions every time you boot.

Jim

But in linux it does it in the different way it is when i open them.

and jigsaws can you please explain that thing to me in more convenient way? thanks.


P.S: i meant explain the process to make them auto mount.

---

### Post by soomro on 2009-04-04
waiting for some one to explain to me how to auto mount all partitions thanks.

---

### Post by oldos2er on 2009-04-04
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by accooper on 2009-04-04
There is an easier way.  Go to install/remove software and search for diskmanager.  This program allows you to mount or boot up with out mounting drives specified by you.

I have been using it since I installed Ubuntu three weeks ago.

:guitar:

Andrew

---

### Post by Rocket2DMn on 2009-04-04
Please be patient and give the community time to respond, you should wait 24 hours before bumping a post to get a response.

That said, if you post the output of the following commands, I would be glad to help you build the appropriate fstab entires:
```
sudo fdisk -l
cat /etc/fstab
mount
sudo blkid
```
If you can identify which partitions you want mounted, please point them out.

---

### Post by soomro on 2009-04-05
This is it.
```
tassaduq@Lost-in-dreams:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb5eeb5ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   c  W95 FAT32 (LBA)
/dev/sda2            2433        9728    58605120    f  W95 Ext'd (LBA)
/dev/sda5            2433        4864    19535008+   7  HPFS/NTFS
/dev/sda6            4865        9728    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16461645

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1999    16056936    7  HPFS/NTFS
/dev/sdb2            2000        9728    62083192+   f  W95 Ext'd (LBA)
/dev/sdb5            2000        4972    23880591    b  W95 FAT32
/dev/sdb6            4973        6553    12699351    7  HPFS/NTFS
/dev/sdb7            6554        6647      755023+  82  Linux swap / Solaris
/dev/sdb8            6648        7394     6000246   83  Linux
/dev/sdb9            7395        9728    18747823+  83  Linux
tassaduq@Lost-in-dreams:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb9
UUID=e43c8a8c-4339-413f-804e-e4dfd2e80d81 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb8
UUID=368c18e5-c085-4fde-bc97-02694120e990 /home           ext3    relatime        0       2
# /dev/sdb7
UUID=8e9918ad-6c98-4880-b947-eaddfdf5e77c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
tassaduq@Lost-in-dreams:~$ mount
/dev/sdb9 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb8 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tassaduq/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tassaduq)

```

---

### Post by Rocket2DMn on 2009-04-05
Thanks.  Can you also please post the output of 
```
sudo blkid
```
Also, which of those partitions do you want to mount automatically?

---

### Post by soomro on 2009-04-05
> **Rocket2DMn said:**
> Thanks.  Can you also please post the output of 
```
sudo blkid
```
Also, which of those partitions do you want to mount automatically?

```
tassaduq@Lost-in-dreams:~$ sudo blkid
/dev/sda1: UUID="50EE-F30B" TYPE="vfat" 
/dev/sda5: UUID="0A108E0C108DFEC7" LABEL="Win7" TYPE="ntfs" 
/dev/sda6: UUID="8ED8D079D8D0614F" LABEL="tassan's world" TYPE="ntfs" 
/dev/sdb1: UUID="5EDC02D6DC02A7FB" LABEL="Windows Xp" TYPE="ntfs" 
/dev/sdb5: LABEL="TASSADUQ" UUID="1094-2721" TYPE="vfat" 
/dev/sdb6: UUID="D448016948014BA4" LABEL="Backup" TYPE="ntfs" 
/dev/sdb7: TYPE="swap" UUID="8e9918ad-6c98-4880-b947-eaddfdf5e77c" 
/dev/sdb8: UUID="368c18e5-c085-4fde-bc97-02694120e990" TYPE="ext3" 
/dev/sdb9: UUID="e43c8a8c-4339-413f-804e-e4dfd2e80d81" TYPE="ext3" 

```

---

### Post by Rocket2DMn on 2009-04-05
Thanks, you still haven't answered the last question though.  Which of the partitions do you want to be mounted automatically?  You have 5 or 6 partitions outside of your root, /home, and swap.  

With that information in hand, where do you want each of them mounted to on your filesystem?  For example:
/media/windows
/media/data
/media/abc
/media/xyz

I need to know which partition you want mounted where in order to help you build the correct fstab entry.

---

### Post by soomro on 2009-04-05
> **Rocket2DMn said:**
> Thanks, you still haven't answered the last question though.  Which of the partitions do you want to be mounted automatically?  You have 5 or 6 partitions outside of your root, /home, and swap.  

With that information in hand, where do you want each of them mounted to on your filesystem?  For example:
/media/windows
/media/data
/media/abc
/media/xyz

I need to know which partition you want mounted where in order to help you build the correct fstab entry.

uh sorry i want to get all the partitions mounted. and i want to mount them into my Home folder? i hope you understand me i mean

/home/windows and replace home with all "media" up there...

---

### Post by Rocket2DMn on 2009-04-05
/media is where we normally mount other partitions, and they can be configured such that you have read/write access to them.  We don't do /home/location because /home is *only* for user's home directories, but you could do /home/yourusername/location.  Please tell me which partitions you would like mounted at which location, example:
/dev/sda1 - /home/username/disk1
/dev/sda5 - /home/username/my_data
and so on and so forth.  Otherwise I can't help you build the fstab entries because I don't know what is on the different partitions.

---

### Post by soomro on 2009-04-05
> **Rocket2DMn said:**
> /media is where we normally mount other partitions, and they can be configured such that you have read/write access to them.  We don't do /home/location because /home is *only* for user's home directories, but you could do /home/yourusername/location.  Please tell me which partitions you would like mounted at which location, example:
/dev/sda1 - /home/username/disk1
/dev/sda5 - /home/username/my_data
and so on and so forth.  Otherwise I can't help you build the fstab entries because I don't know what is on the different partitions.

what does disk1 and my_data mean?

ok i want to mount them in /media

---

### Post by Rocket2DMn on 2009-04-05
Those are just examples of subfolders to mount the partitions at.  Where do they mount now when you mount them manually?  Something like /media/disk ?  That name isn't very descriptive, people usually like meaninful names in their mount points.  For example, I mount my Windows NTFS partition at /media/windows, and my external USB drive at /media/usbdisk.

---

### Post by soomro on 2009-04-05
> **Rocket2DMn said:**
> Those are just examples of subfolders to mount the partitions at.  Where do they mount now when you mount them manually?  Something like /media/disk ?  That name isn't very descriptive, people usually like meaninful names in their mount points.  For example, I mount my Windows NTFS partition at /media/windows, and my external USB drive at /media/usbdisk.

Ok just give them sequential names likes disk_1 disk_2  and i will replace them accordingly myself.

---

### Post by Rocket2DMn on 2009-04-05
Ok then, I see that some drives already have labels, so I will base my mount points on those.  Please note that mount points declared in fstab can't have spaces or special characters in them.  I have done my best to keep your names, including character case.

First open fstab for editing
```
gksudo gedit /etc/fstab
```

Now add the following to the file:
```

# /dev/sda1
UUID=50EE-F30B /media/disk_a1 vfat defaults 0 0
# /dev/sda5
UUID=0A108E0C108DFEC7 /media/Win7 ntfs-3g defaults,locale=en_US.utf8 0 0
# /dev/sda6
UUID=8ED8D079D8D0614F /media/tassan ntfs-3g defaults,locale=en_US.utf8 0 0
# /dev/sdb1
UUID=5EDC02D6DC02A7FB /media/WindowsXP ntfs-3g defaults,locale=en_US.utf8 0 0
# /dev/sdb5
UUID=1094-2721 /media/TASSADUQ vfat defaults 0 0
# /dev/sdb6
UUID=D448016948014BA4 /media/Backup ntfs-3g defaults,locale=en_US.utf8 0 0

```

For the NTFS partitions, I gave a relatively simple *options* column where you see "defaults,locale=en_US.utf8".  On my own system I use
```
auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137
```
instead which gives 750 (rwxr-x----) linux type permissions on directories and 640 (rw-r-----) permissions on files, and mounts owned by my username (uid=1000) and group "users" (gid=100).  You can use whatever you like, see [uhelp]community/Fstab[/uhelp] for more info.

Also, you may need to replace "locale=en_US.utf8" with your own locale (I don't know if you're using the English version, or a Pakistani version).  I don't know the locale name for Pakistan, try running
```
locale
```

Alternatively, for FAT32 and FAT16 (vfat) I use "rw,nosuid,nodev,shortname=mixed,uid=1000".  It's a matter of preference.

Save and close the file.  Before you mount, you must create the mount points in column two using
```
sudo mkdir /media/*location*
```
where *location* is the specific mount point.  Remember that the directory names are case sensitive.  Example:
```
sudo mkdir /media/Win7
```

Now mount all partitions:
```
sudo mount -a
```

Everything should mount correctly and nothing should be output to the terminal.  If you get errors, please post them here.

---

### Post by soomro on 2009-04-06
leme try

---

### Post by soomro on 2009-04-06
Is this correct?
if not forgive me, its so confusing to understand the columns :(
```

d# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb9
UUID=e43c8a8c-4339-413f-804e-e4dfd2e80d81 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb8
UUID=368c18e5-c085-4fde-bc97-02694120e990 /home           ext3    relatime        0       2
# /dev/sdb7
UUID=8e9918ad-6c98-4880-b947-eaddfdf5e77c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda1
UUID=50EE-F30B /media/disk_a1 vfat defaults 0 0
# /dev/sda5
UUID=0A108E0C108DFEC7 /media/Win7 ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137
# /dev/sda6
UUID=8ED8D079D8D0614F /media/tassan ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137
# /dev/sdb1
UUID=5EDC02D6DC02A7FB /media/WindowsXP ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137
# /dev/sdb5
UUID=1094-2721 /media/TASSADUQ vfat defaults 0 0
# /dev/sdb6
UUID=D448016948014BA4 /media/Backup ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137
```

```
tassaduq@Lost-in-dreams:~$ sudo mount -a
[mntent]: line 1 in /etc/fstab is bad
mount: mount point /media/disk_a1 does not exist
fuse: failed to access mountpoint /media/Win7: No such file or directory
fuse: failed to access mountpoint /media/tassan: No such file or directory
fuse: failed to access mountpoint /media/WindowsXP: No such file or directory
mount: mount point /media/TASSADUQ does not exist
fuse: failed to access mountpoint /media/Backup: No such file or directory
```

did i do it the right way?
if not sorry i am not that much nerdy :lolflag:

---

### Post by stimpyaw on 2009-04-07
I have been banging my head against the wall for a while know on how to mount my 2nd drive.  I just want to say thank you for the clear and easy instructions. fstab RULES!!! LOL

Thanks!


> **Rocket2DMn said:**
> Ok then, I see that some drives already have labels, so I will base my mount points on those.  Please note that mount points declared in fstab can't have spaces or special characters in them.  I have done my best to keep your names, including character case.

First open fstab for editing
```
gksudo gedit /etc/fstab
```Now add the following to the file:
```

# /dev/sda1
UUID=50EE-F30B /media/disk_a1 vfat defaults 0 0
# /dev/sda5
UUID=0A108E0C108DFEC7 /media/Win7 ntfs-3g defaults,locale=en_US.utf8 0 0
# /dev/sda6
UUID=8ED8D079D8D0614F /media/tassan ntfs-3g defaults,locale=en_US.utf8 0 0
# /dev/sdb1
UUID=5EDC02D6DC02A7FB /media/WindowsXP ntfs-3g defaults,locale=en_US.utf8 0 0
# /dev/sdb5
UUID=1094-2721 /media/TASSADUQ vfat defaults 0 0
# /dev/sdb6
UUID=D448016948014BA4 /media/Backup ntfs-3g defaults,locale=en_US.utf8 0 0

```For the NTFS partitions, I gave a relatively simple *options* column where you see "defaults,locale=en_US.utf8".  On my own system I use
```
auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137
```instead which gives 750 (rwxr-x----) linux type permissions on directories and 640 (rw-r-----) permissions on files, and mounts owned by my username (uid=1000) and group "users" (gid=100).  You can use whatever you like, see [uhelp]community/Fstab[/uhelp] for more info.

Also, you may need to replace "locale=en_US.utf8" with your own locale (I don't know if you're using the English version, or a Pakistani version).  I don't know the locale name for Pakistan, try running
```
locale
```Alternatively, for FAT32 and FAT16 (vfat) I use "rw,nosuid,nodev,shortname=mixed,uid=1000".  It's a matter of preference.

Save and close the file.  Before you mount, you must create the mount points in column two using
```
sudo mkdir /media/*location*
```where *location* is the specific mount point.  Remember that the directory names are case sensitive.  Example:
```
sudo mkdir /media/Win7
```Now mount all partitions:
```
sudo mount -a
```Everything should mount correctly and nothing should be output to the terminal.  If you get errors, please post them here.

---

### Post by Rocket2DMn on 2009-04-07
soomro, you need to create the directories first using
```
sudo mkdir /media/*location*
```
for instance,
```
sudo mkdir /media/disk_a1
sudo mkdir /media/Win7
```
and so on.  Then you can run the mount command.

---

### Post by soomro on 2009-04-07
> **Rocket2DMn said:**
> soomro, you need to create the directories first using
```
sudo mkdir /media/*location*
```
for instance,
```
sudo mkdir /media/disk_a1
sudo mkdir /media/Win7
```
and so on.  Then you can run the mount command.

i did that put this in fstab

```

d# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=50EE-F30B /media/disk_a1 vfat defaults 0 0
# /dev/sda5
UUID=0A108E0C108DFEC7 /media/Win7 ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137
# /dev/sda6
UUID=8ED8D079D8D0614F /media/tassan ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137
# /dev/sdb1
UUID=5EDC02D6DC02A7FB /media/WindowsXP ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137
# /dev/sdb5
UUID=1094-2721 /media/TASSADUQ vfat defaults 0 0
# /dev/sdb6
UUID=D448016948014BA4 /media/Backup ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137
# /dev/sdb9
UUID=e43c8a8c-4339-413f-804e-e4dfd2e80d81 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb8
UUID=368c18e5-c085-4fde-bc97-02694120e990 /home           ext3    relatime        0       2
# /dev/sdb7
UUID=8e9918ad-6c98-4880-b947-eaddfdf5e77c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

then i get this?
```
tassaduq@Lost-in-dreams:~$ sudo mount -a
[mntent]: line 1 in /etc/fstab is bad
fuse: failed to access mountpoint /media/Win7: No such file or directory
fuse: failed to access mountpoint /media/WindowsXP: No such file or directory
fuse: failed to access mountpoint /media/Backup: No such file or directory

```

i created the directories then what is the error?
sorry  i am being so stupid.

---

### Post by soomro on 2009-04-10
:mad:bump

---

### Post by Rocket2DMn on 2009-04-10
Sorry, I missed your last post.  You have an extra character in your fstab file at the beginning of the very first line
```
[COLOR="Red"]d[/COLOR]# /etc/fstab: static file system information.
```
Please remove the "d".

Also, you are missing two "columns" at the end of some of your rows, you need the "0 0" after your four ntfs entries.

```
UUID=0A108E0C108DFEC7 /media/Win7 ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137 [COLOR="red"]0 0[/COLOR]
# /dev/sda6
UUID=8ED8D079D8D0614F /media/tassan ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137 [COLOR="red"]0 0[/COLOR]
# /dev/sdb1
UUID=5EDC02D6DC02A7FB /media/WindowsXP ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137 [COLOR="red"]0 0[/COLOR]
# /dev/sdb6
UUID=D448016948014BA4 /media/Backup ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137 [COLOR="Red"]0 0[/COLOR]

```

Save and close, then try the mount command again.

---

### Post by Slim Odds on 2009-04-10
> **Rocket2DMn said:**
> /media is where we normally mount other partitions, and they can be configured such that you have read/write access to them. 

Actually, /media is for transient mounts like USB flash drives, CD-ROM, etc.

If you're mounting something on a permanent basis, it would be more appropriate to find a decent name and mount it there.

For example, I have an extra internal drive that I mount as /data

---

### Post by Rocket2DMn on 2009-04-10
> **Slim Odds said:**
> Actually, /media is for transient mounts like USB flash drives, CD-ROM, etc.

If you're mounting something on a permanent basis, it would be more appropriate to find a decent name and mount it there.

For example, I have an extra internal drive that I mount as /data

Mounting to a folder immediately on the root of the filesystem isn't really best practices.  Ubuntu tends to place things at /media, so I stick with that convention.  /mnt is also acceptable, and is often accepted as the place to put static mounts.

---

### Post by Slim Odds on 2009-04-10
> **Rocket2DMn said:**
> Mounting to a folder immediately on the root of the filesystem isn't really best practices.  Ubuntu tends to place things at /media, so I stick with that convention.  /mnt is also acceptable, and is often accepted as the place to put static mounts.

I was going to mention /mnt, but the LSB file system specification states that it is for temporary mounts ([http://www.pathname.com/fhs/pub/fhs-2.3.html#MNTMOUNTPOINTFORATEMPORARILYMOUNT](http://www.pathname.com/fhs/pub/fhs-2.3.html#MNTMOUNTPOINTFORATEMPORARILYMOUNT))

Since mounting a drive for specific use outside of the standard file system is, by definition, non-standard, I think that you should put it wherever you would like it.

---

### Post by soomro on 2009-04-12
> **Rocket2DMn said:**
> Sorry, I missed your last post.  You have an extra character in your fstab file at the beginning of the very first line
```
[COLOR="Red"]d[/COLOR]# /etc/fstab: static file system information.
```
Please remove the "d".

Also, you are missing two "columns" at the end of some of your rows, you need the "0 0" after your four ntfs entries.

```
UUID=0A108E0C108DFEC7 /media/Win7 ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137 [COLOR="red"]0 0[/COLOR]
# /dev/sda6
UUID=8ED8D079D8D0614F /media/tassan ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137 [COLOR="red"]0 0[/COLOR]
# /dev/sdb1
UUID=5EDC02D6DC02A7FB /media/WindowsXP ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137 [COLOR="red"]0 0[/COLOR]
# /dev/sdb6
UUID=D448016948014BA4 /media/Backup ntfs-3g auto,users,uid=1000,gid=100,locale=en_US.utf8,dmask=027,fmask=137 [COLOR="Red"]0 0[/COLOR]

```

Save and close, then try the mount command again.



thanks a lot got it,
but i was missing only one thing that you did not note and that was that i needed to put the letters as case sensitives XD
and i was putting sometimes lower case and sometimes upper case letters. but yea thanks alot it was so easy but never mind i was so dumb:lolflag:

---

### Post by soomro on 2009-04-12
> **Slim Odds said:**
> I think that you should put it wherever you would like it.

He said the same XD
i did as he said cause i think he is more experienced then me...

---

