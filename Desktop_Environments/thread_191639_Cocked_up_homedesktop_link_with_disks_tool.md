---
title: "Cocked up /home/desktop link with disks tool"
date: 2006-06-07
forum: Desktop Environments
---

### Post by xenomorph99 on 2006-06-07
Hi,

I added a harddisk, post install of Ubuntu 6.06. I then tried to access the harddisk via the 'disks' tool but couldn't access it (it was something like /dev/temp/hda-1...or similar). I could browse it and "attempt to set a link" to it but no access was obtainable.

As I was closing the disks tool, I seem to have clicked apply/ok with the link '/desktop/home' "applied" to the harddisk I couldn't access previous. 

Subsequently, I could not launch any applications because I didn't have permission to access "/desktop/home somthing" nor could I log on following a reboot.

Easy way out of this?

I've only been running Ubuntu for one evening and managed to wreck it..That never happened with Windows ;)


Ta,
Xeno

---

### Post by mlind on 2006-06-07
Could you post specific error message ?

Something may have accidently changed the ~/Desktop folder permissions.
You can access tty terminal (wihout graphical interface) by pressing
```

Ctrl + Alt + F1

```
(Ctrl + Alt + F7 to get back to graphical mode)

then log in using you username and password. Post result of 
```

ls -ld ~/Desktop

```

---

### Post by xenomorph99 on 2006-06-07
cheers for the quick response.

I don't think I *changed* the permissions but you might be right. I think that the desktop is somehow mapped to the drive I couldn't access and, because I didn't have the right permissions to access that drive, it's all stopped working (I seem to recall a message as such saying that I didn't have the right permissions to access the drive). 

I'll try what you said, though - thanks for the help :)

Regardless, what I don't understand is why a) Ubuntu didn't "pick up the new drive" being added (in terms of being able to access it like the other HDD....read only, at least) and/or b) why I can see it but cannot access it.

Ta,
Xeno

---

### Post by mlind on 2006-06-07
I don't know. I haven't ever added any filesystems using Disks Admin tool.
There's wiki articles that might help you [https://wiki.ubuntu.com/DrivesAndPartitions](https://wiki.ubuntu.com/DrivesAndPartitions)

Adding a new harddisk is basically just adding new line on /etc/fstab file.

---

### Post by xenomorph99 on 2006-06-07
OK, I'm back into Ubuntu. Seems that, oddly, on the *second* reboot, it appears to have rectified itself.

For reference, the desktop had attributes 
drwxr-xr-x

Out of interest, do I need to mess about with fstab to select which partitions/drives I want Ubuntu to see (two drives, set up as follows:

hda1 - main boot drive - partition 1 = Windows XP
hda1 -                           - partition 2 = Win XP 'Swap'
hdb1 - Second drive     - 7 partitions.
4 NTFS
1 EXT (Ubuntu)
1 Linux Swap
1 FAT32 (Xfer area between Ubuntu and Windows)

I only really want to access the FAT32 and hda1 first partition. The latter just to play mp3s from.

Ta,
Xeno

EDIT: Will check out that and look into fstab....

---

### Post by mlind on 2006-06-07
to get list of all partitions and corresponding device names, use
```

sudo fdisk -l

```

You need to create a mount point for the FAT32 drive, usually /media or /mnt
are good places. On Dapper, there's special group called 'plugdev' which is group
for 'pluggable devices?' dunno, but it seems be group permissions for my NTFS share.

Your fstab entry could look like
```

/dev/hda1       /media/share  vfat    iocharset=utf8,umask=000,gid=46   0       0

```

where device name is /dev/hda1. You must create /media/share manually, using
```

sudo mkdir -p /media/share

```

Only use *gid=46* if your /etc/group file contains entry that looks like 'plugdev: x:46:haldaemon:..'.

---

### Post by xenomorph99 on 2006-06-10
Hi,

Thanks for the reply. I tried what you suggested but it didn't appear to work.

What I get with fdisk is:

> Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/hda2           16709       19457    22081342+   f  W95 Ext'd (LBA)
/dev/hda5           16709       19457    22081311    7  HPFS/NTFS

Disk /dev/hdc: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        1275    10241406    7  HPFS/NTFS
/dev/hdc2            1276        4982    29776477+   f  W95 Ext'd (LBA)
/dev/hdc5            1276        1530     2048256    7  HPFS/NTFS
/dev/hdc6            1531        3634    16900348+   7  HPFS/NTFS
/dev/hdc7   *        3635        4527     7172991   83  Linux
/dev/hdc8            4528        4593      530113+  82  Linux swap / Solaris
/dev/hdc9            4594        4982     3124611    b  W95 FAT32

So, I tried to edit the fstab to:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc1       /media/hdc1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdc5       /media/hdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdc6       /media/hdc6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdc9       /media/hdc9     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdc8       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/share    ntfs    defaults,nls=utf8,umask=007,gid=46 0     

Obviously, I just copied the line from another NTFS partition but referred to it as media/share as you suggested.

After trying 'sudo mkdir -p /media/share', I seem to get a directory but it's empty...it's certainly not 'pointing' to my hda.

I also tried '/dev/hda1       /dev/hda1    ntfs    defaults,nls=utf8,umask=007,gid=46 0' in the fstab file but that didn't appear to let me access the hda1 either.

Do I need to reboot following each change to the fstab or can I 'force' it to remount etc via the command line?

Ta,
Xeno

---

### Post by xenomorph99 on 2006-06-10
Ah, after the reboot, it's mounted it....:)

Thanks for the help.

Ta,
Xeno

---

### Post by mlind on 2006-06-10
[QUOTE=xenomorph99]Ah, after the reboot, it's mounted it....:)

Thanks for the help.

Ta,
Xeno[/QUOTE]

yeah, /etc/fstab entry looked good, *sudo mount /media/share* should have done
it. Just make sure you actually have exisiting group called 'plugdev' with GID 46.

When you want another useraccount to gain access on that ntfs share, just add
it to plugdev group.

---

