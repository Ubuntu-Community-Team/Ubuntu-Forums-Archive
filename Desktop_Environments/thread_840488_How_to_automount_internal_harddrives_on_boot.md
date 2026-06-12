---
title: "How to automount internal harddrives on boot"
date: 2008-06-25
forum: Desktop Environments
---

### Post by philidox on 2008-06-25
Its not a big deal but everytime I reboot my computer I have to under "Places" and select a my hard drive in order to mount them on my desktop.  How to I enable this automatically so I can don't have to do that anymore.

---

### Post by ilrudie on 2008-06-25
> **philidox said:**
> Its not a big deal but everytime I reboot my computer I have to under "Places" and select a my hard drive in order to mount them on my desktop.  How to I enable this automatically so I can don't have to do that anymore.
The file that controls static volumes is /etc/fstab.  Locate the line for the drive and see if it has a noauto option.  It also may be commented out (lines beginning with # are comments)  If it does not appear in the file you will need to create an entry for it.  If you don't know how post back and I can help you create the proper entry.

---

### Post by philidox on 2008-06-25
> **ilrudie said:**
> The file that controls static volumes is /etc/fstab.  Locate the line for the drive and see if it has a noauto option.  It also may be commented out (lines beginning with # are comments)  If it does not appear in the file you will need to create an entry for it.  If you don't know how post back and I can help you create the proper entry.

I don't mind doing it the with cli but isnt there a gui program that will do it for me? Here is my fstab output

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by ilrudie on 2008-06-25
Looks like its not in the fstab file.  You will need to add it.  In order to add it you will need to know the block device (/dev/<something>), the filesystem type (probably ntfs or fat32 if its a windows disk or ext3 if its a GNU/Linux disk) and a path to where you want it (/media/<drive_name> if you want it to show up on your desktop).

To find the block device run a df -kh after mounting it from places.  It will show you all mounted filesystems, their usage and mount point.  Post the line that contains the disk you want to mount.

---

### Post by earthmeLon on 2008-06-25
Hey!  This should be easy to fix, and you'll learn a little about how mounting works :D

Once you've started the computer and you've manually mounted your drive, open a terminal and run:

```
mount
```

This will display all of your currently mounted drives.  For example:

```
/dev/sdb1 on /media/Boomer type fuseblk
```

This shows you what the drive is, and where it is currently being mounted to.  Fuseblk and ntfs/ntfs-3g are all NTFS partiton types, which is what your partition probably is if it was created with Windows. Now, open your /etc/fstab and append the following entry:

**To Open**
```
gksudo gedit /etc/fstab
```

**What to add**
```
/dev/**sdb1** /media/**Erebus2** ntfs-3g rw,user,auto 0 0
```

Save the file and on next boot, it should be all good :D

**Note:**
* You need to change ntfs-3g to whatever partition type you are mounting :D

* This will mount the drive so that any user has access to it (unless you set permissions otherwise)

---

### Post by the lush on 2008-06-25
Hi, these instructions are pretty clear, however my insecurity is also pretty intense. In response to the **mount** query I find my drive:

/dev/sda2 on /media/Drivename type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

I therefore assume that in the fstab thing I need to add

/dev/sda2 on /media/Drivename fuseblk rw,**auto**,nosuid,nodev,noatime,allow_other,blksize=4096

I am using 8.04. 

Thanks in advance for any help with this.

---

