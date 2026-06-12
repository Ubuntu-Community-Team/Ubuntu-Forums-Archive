---
title: "Mounted partitions not accessable in Computer"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Pyr3 on 2006-06-05
I had a nice message posted but GNOME randomly crashed so let's try again!

I've etc/fstab'd all my windows (fat & ntfs) partitions.  They work flawlessly with full RW access.

However, the drives in Places => Computer (with the exception of my one FAT formatted drive) fail to go to the proper mount point when double clicked, with the error that:


mount: according to mtab, /dev/hdb1
is already mounted on /mnt/music
mount failed


They're all mounted properly, so it strikes me as odd why only the NTFS drives should do this.

I can't seem to find what exactly it is i need to fix to make it work...

Would deleting the shortcut and recreating a symlink work?


_**Breakthrough/Solution/Edit:**_

I figured it out:

Every one of those icons in Computer points to /media/<partion>, from what i saw in the /etc/fstab file

So, all i had to do was:

```
cd /media
sudo mkdir hdb#
```

Where # is the partion number assigned by linux, for each of the NTFS partions.

Followed by:

```
sudo gedit /etc/fstab
```

Adding the line:

```
/dev/hdb#       /media/hdb#     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```

Again, replacing # with the partion number.

Reboot - BAM! There they all are.


Final /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb2       /media/hdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb3       /media/hdb3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by kb3hkg on 2006-06-05
can you post ur fstab file? I am still having issues getting RW access to work on such drives, and my threads are continually abandoned by those who start trying to help

---

### Post by Pyr3 on 2006-06-06
etc/fstab contents:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1    /mnt/apache    vfat    auto,gid=1001,umask=0007    0    0
/dev/hda2    /mnt/more_space    ntfs-fuse    auto,gid=1001,umask=0007    0    0
/dev/hdb1    /mnt/music    ntfs-fuse    auto,gid=1001,umask=0007    0    0
/dev/hdb2    /mnt/anime    ntfs-fuse    auto,gid=1001,umask=0007    0    0
/dev/hdb3    /mnt/movies    ntfs-fuse    auto,gid=1001,umask=0007    0    0
/dev/sda1    /mnt/windows    ntfs-fuse    auto,gid=1001,umask=0007    0    0
/dev/sda2    /mnt/stuffs    ntfs-fuse    auto,gid=1001,umask=0007    0    0
```

---

### Post by kb3hkg on 2006-06-06
what mount point is it going to since you said it goes to the wrong one

---

### Post by Pyr3 on 2006-06-07
> what mount point is it going to since you said it goes to the wrong one


If you look at the error message above it's not going to the wrong mount point.

It's saying that it can't mount the drive because it's already mounted.  The error doesn't occur when i mount the FAT drive, only the NTFS ones for some reason.  It's like it won't accept the fact that it's mounted or something.

N.B: If i unmount/remount the FAT drive under a new mount point (say from /mnt/apache to mnt/boogers) it still works.

---

### Post by kb3hkg on 2006-06-07
then it sounds like the drive is mounted, is the problem just that you cannot access it?

---

### Post by Pyr3 on 2006-06-07
It is accessable.

> They're all mounted properly, so it strikes me as odd why only the NTFS drives should do this.

The thing is is i'm just being a lazy bastard who doesn't want to have to navigate to the filesystem/mnt/<folder> everytime i want to view/execute a file from that partition - as well as comment on a strange glitch.

---

### Post by kb3hkg on 2006-06-08
Ah ok, well in that case to take care of laziness I'd say either create a link, or write a quick script. Either way can get u there a little more easily.

But you are right that is an interesting glitch, but since when have linux and ntfs ever worked together nicely?

---

### Post by Pyr3 on 2006-06-10
[QUOTE=kb3hkg]...but since when have linux and ntfs ever worked together nicely?[/QUOTE]

When i used my old distro CD's and Windows patch CD's for target practice.

PULL!




Anyway.

I reinstalled Dapper because the Xgl/Compiz was causing some things on the system to work strangely after the last update and after i uninstalled it i had a bunch of problems in X - along with the wobble effect giving me motion sickness.  Yeah, i know that was a real windows-like move (problem? reformat!).

So after reinstalling i noticed something odd (linux never installs the same way twice for me, don't ask why).  After first boot, on my desktop were the two NTFS partitions on the drive - Stuffs and Windows!  It had read and execute privilagesand belonged to user "root" and group "plugdev."  I am a member of plugdev.

However - After reconnecting my other two drives (i boot from a SCSI), the other NTFS partitions on the other drives do NOT auto-mount.  They give the error:


**Unable to mount selected volume**
error: device /dev/hdb2 is not removable
error: could not execute pmount


So now i just stare blankly and drool.

---

