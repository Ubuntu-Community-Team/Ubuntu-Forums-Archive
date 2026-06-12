---
title: "Viewing Vista Partition in Ubuntu?"
date: 2009-03-26
forum: General Help
---

### Post by AnDrE_pSp on 2009-03-26
I've recently done a partition of Vista/Ubuntu 8.10 with Vista installed first.

I know need to access my Vista partition because It simple failed and won't boot.

Anyway of accessing the Vista partition in Ubuntu?

Thanks.

---

### Post by mb_webguy on 2009-03-26
It should show up in the Places menu.  If so, clicking on it should automatically mount it.

Otherwise, you'll have to use the command "sudo fdisk -l" to determine the device associated with the partition, and then mount it manually with "sudo mkdir /mnt/vista; sudo mount /dev/*xxxn* /mnt.vista", where *xxxn* is the device.

---

### Post by AnDrE_pSp on 2009-03-26
> **mb_webguy said:**
> It should show up in the Places menu.  If so, clicking on it should automatically mount it.

Otherwise, you'll have to use the command "sudo fdisk -l" to determine the device associated with the partition, and then mount it manually with "sudo mkdir /mnt/vista; sudo mount /dev/*xxxn* /mnt.vista", where *xxxn* is the device.

It keeps asking me for the sudo password

[IMG]http://i39.tinypic.com/33yjddc.png[/IMG]

Then says "Cannot mount volume"

[IMG]http://i39.tinypic.com/343rksp.png[/IMG]

```
google@MSHOME:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe46de46d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       50975   409455584+   7  HPFS/NTFS
/dev/sda2           50976       77825   215672625    5  Extended
/dev/sda5           50976       76731   206885038+  83  Linux
/dev/sda6           76732       77825     8787523+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    c  W95 FAT32 (LBA)
google@MSHOME:~$ 


```

What do I do now?

EDIT:

```
google@MSHOME:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe46de46d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       50975   409455584+   7  HPFS/NTFS
/dev/sda2           50976       77825   215672625    5  Extended
/dev/sda5           50976       76731   206885038+  83  Linux
/dev/sda6           76732       77825     8787523+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    c  W95 FAT32 (LBA)
google@MSHOME:~$ sudo mkdir /mnt/vista
mkdir: cannot create directory `/mnt/vista': File exists
google@MSHOME:~$ sudo mount /dev/sda1/mnt.vista
mount: can't find /dev/sda1/mnt.vista in /etc/fstab or /etc/mtab
google@MSHOME:~$ 

```

---

### Post by mb_webguy on 2009-03-26
So what happens when you enter your password?  The password for administrative tasks (i.e. sudo) is your login password.

---

### Post by AnDrE_pSp on 2009-03-26
> **mb_webguy said:**
> So what happens when you enter your password?  The password for administrative tasks (i.e. sudo) is your login password.

"Cannot mount volume"

Screen 2 is what it looks like.

---

### Post by mb_webguy on 2009-03-26
Ah, sorry.  I misread your previous post.  In that case, your solution is actually in that second screenshot.  You need to use the command "sudo mount -t ntfs-3g /dev/sda1 /media/disk -o force".  

The ntfs filesystem is a journaling filesystem, and while ntfs-3g can't handle journaling, it *can* tell when there is uncommitted information in the journal, and refuses to mount it.  Normally, you should boot into Windows to take care of the problem, but since you can't do that in this case, you can use the "force" option of mount to, um... force it to mount the partition.

---

### Post by AnDrE_pSp on 2009-03-26
```
google@MSHOME:~$ sudo mount -t ntfs-3g /dev/sda1 /media/disk -o force
[sudo] password for google: 
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/disk: No such file or directory
google@MSHOME:~$ 
```

---

### Post by mb_webguy on 2009-03-26
> **AnDrE_pSp said:**
> ```
google@MSHOME:~$ sudo mount -t ntfs-3g /dev/sda1 /media/disk -o force
[sudo] password for google: 
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/disk: No such file or directory
google@MSHOME:~$ 
```

"sudo mkdir /media/disk", then use the mount command.

---

### Post by AnDrE_pSp on 2009-03-26
Thanks it works now :popcorn:

---

### Post by betaraywil on 2009-03-26
I'm having more or less the same problem, attempting to recover data from a Vista partition using a live CD boot disk thing.  Entering the suggested code (sudo mount -t ntfs-3g /dev/sda1 /media/60.0 GB Media -o force), I get this shot back at me:

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


And I have no idea what to make of this.  If I'm merely hoping to do some data recovery before reformatting, what on earth do I do here?  (Sorry if this is a bit elementary, I've just only been using Ubuntu for the day, and haven't an idea what I'm doing).

---

### Post by coffeecat on 2009-03-26
The mount command is throwing a standard help message at you. It doesn't like what you've typed in. Compare mb_webguy's and your texts:

> **mb_webguy said:**
> sudo mount -t ntfs-3g /dev/sda1 /media/disk -o force

> **betaraywil said:**
> sudo mount -t ntfs-3g /dev/sda1 /media/60.0 GB Media -o force

I assume the mountpoint for your NTFS drive is /media/60.0 GB Media, which includes spaces. If I'm right, that's your problem. You need to escape your spaces with backslashes. Try:

```
sudo mount -t ntfs-3g /dev/sda1 /media/60.0\ GB\ Media -o force
```**Edit:** but just a thought. The OP has solved their problem, but isn't it possible to boot up Vista in safe mode in order to do a filesystem repair? You certainly could in XP, so it must be possible in Vista. Otherwise there will be thousands of borked and unrepairable Windows systems everywhere. Oh, wait a minute... :?

---

### Post by betaraywil on 2009-03-26
It's a rather long story, but yeah, my Vista install is, as you say, "b0rked."  

But that did work.  Thanks a ton!

---

