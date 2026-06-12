---
title: "i cant figure out why my partitions wont mount"
date: 2005-12-31
forum: General Help
---

### Post by ren wins on 2005-12-31
here's my fstab
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hdb6       /media/hdb6     ntfs    defaults        0       0
/dev/hdb7       /media/hdb7     ntfs    defaults        0       0
/dev/hdb8       /media/hdb8     vfat    defaults        0       0
/dev/hdb9       /media/hdb9     vfat    defaults        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 	/media/windows 	ntfs 	umask=0222 	0 	0
/dev/hdb6 	/media/noise 	ntfs 	umask=0222 	0 	0
/dev/hdb7 	/media/eyes 	ntfs 	umask=0222 	0 	0
/dev/hdb8	/media/static	vfat	umask=000	0	0
/dev/hdb9	/media/support	vfat	umask=000	0	0


and here's mount
> 
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/hda1 on /media/hda1 type ntfs (rw)
/dev/hdb6 on /media/hdb6 type ntfs (rw)
/dev/hdb7 on /media/hdb7 type ntfs (rw)
/dev/hdb8 on /media/hdb8 type vfat (rw)
/dev/hdb9 on /media/hdb9 type vfat (rw)
/dev/hdb8 on /media/static type vfat (rw,umask=000)
/dev/hdb9 on /media/support type vfat (rw,umask=000)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)


i've been staring at my fstab for way too long trying to figure it out
it SHOULD be right, i copied it straight from the help guide...

it's got me stumped tho :(

---

### Post by hajk on 2005-12-31
You would do well to revert to an old Linux trick of consulting a man-page, in this case "man fstab". One of the things it says is that various programmes, like mount, iterate sequentially through /etc/fstab. Now think about what happens in the case of, say, /dev/hda1: first you try to mount this partition on mount point /media/hda1 (as an NTFS file system) using defaults options; then, a little later, you try to mount it again at mount point /media/windows with as only option umask=0222. That's asking for trouble, in my opinion, mounting a partition at two mount points, in the latter case without sufficient accessing options...

What's wrong with only having one line in /etc/fstab for /dev/hda1, something like: 

/dev/hda1    /media/windows  ntfs    ro,users,noauto,umask=0222  0       0

Note also: 
1. I'm suggesting "ro", since writing to an NTFS partition is still, in my opinion, a somewhat dicey issue:( 
2. I'm suggesting "noauto", otherwise you might as well stick with using Windows ;)  you mount by clicking on it in Nautilus.

And similarly for other duplicate lines you have in /etc/fstab.

---

