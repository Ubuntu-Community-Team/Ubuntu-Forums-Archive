---
title: "Can't access my ntfs partitions!"
date: 2006-06-11
forum: Desktop Environments
---

### Post by karlsson88 on 2006-06-11
Hi!

I just installed Ubuntu with gnome and i can't access my "old" ntfs partitions which i used in windows.  I just get this error messages;

"The folder contents could not be displayed.

You do not have the permissions necessary to view the contents of "disks-conf-sdb1". "

](*,) 

Can someone tell me what to do? I don't want to reformat it because i have a lot o things a need on that partition.

---

### Post by olsonar on 2006-06-11
could you post the contents of yout /etc/fstab file?

---

### Post by karlsson88 on 2006-06-11
[QUOTE=olsonar]could you post the contents of yout /etc/fstab file?[/QUOTE]

Yeah sure..


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/windows  ntfs    nls=utf8,umask=0222 0 0

---

### Post by aysiu on 2006-06-11
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Giffo on 2006-06-11
Hi - another Ubuntu 6.06 'newbie' here.   have tried a few 'distros' but keep comng back to Ubuntu and upgraded to 6.06 last week. I have the same problem with accessing XP NTFS partitions.  Tried a lot of stuff but :(

I would appreciate some help here.  Thanks!!

Peter

---

### Post by sarhento_lobo on 2006-06-11
Did the tips in aysiu's link help?

---

### Post by elbryan on 2006-06-11
Uhm .. are you sure you can have a duplicate mount?
```

/dev/sdb1 /media/sdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sdb1 /media/windows ntfs nls=utf8,umask=0222 0 0

```

I'll post you my fstab:
```

/dev/sdb6       /               ext2    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb5       /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb8       /media/sdb8     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

I can see and surf all my ntfs partition ..
Maybe you have forgotten the "defaults" ..

---

### Post by sarhento_lobo on 2006-06-11
aysiu's link as well as the one in the Ubuntu wiki ([https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)) should work, since this is a standard operation. Are any of the steps producing errors?

---

### Post by Giffo on 2006-06-11
[QUOTE=sarhento_lobo]Did the tips in aysiu's link help?[/QUOTE]
Hi there, I have tried again and 6.06 now 'sees' HDA1 but I am now stuck with permissions problem.  It seems I do not have the permissions to access the disk.  Hmmmmm.   There is an answer there somewhere.  Thanks for the help so far guys.......  Learning curves for me....

---

### Post by Giffo on 2006-06-11
[QUOTE=Giffo]Hi there, I have tried again and 6.06 now 'sees' HDA1 but I am now stuck with permissions problem.  It seems I do not have the permissions to access the disk.  Hmmmmm.   There is an answer there somewhere.  Thanks for the help so far guys.......  Learning curves for me....[/QUOTE]

OK.... aditional info here...

my fstab file reads like this.....  Is there something glaringly obvious I am missing??? (Probabaly answer is YES, but I am getting there....)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /media/hda1 ntfs-fuse auto,gid=1002,umask=0002 0 0

---

### Post by sarhento_lobo on 2006-06-11
Could you try:

sudo umount /dev/hda1

then 

sudo mount /dev/hda1 -t ntfs -o defaults,ro,nls=utf8,umask=0222 {mount_point}

then sudo mount -a?

I'm thinking the "ro" option might be necessary. (the "{mount_point}" should be replaced by the directory you want to mount it against)

---

### Post by Giffo on 2006-06-11
[QUOTE=sarhento_lobo]Could you try:

sudo umount /dev/hda1

then 

sudo mount /dev/hda1 -t ntfs -o defaults,ro,nls=utf8,umask=0222 {mount_point}

then sudo mount -a?

I'm thinking the "ro" option might be necessary. (the "{mount_point}" should be replaced by the directory you want to mount it against)[/QUOTE]

Thanks for your help here but this did not work.  The HDA1 icon on the desktop has disappeared though....

---

### Post by Giffo on 2006-06-11
[QUOTE=Giffo]Thanks for your help here but this did not work.  The HDA1 icon on the desktop has disappeared though....[/QUOTE]
OK fiddled a bit more here, the HDA1 icon has now re-appeared on the desktop but now labled /tmp/disks-conf-hda1 and still not accessible due to permissions... hmmmmmmmmmm  coffee and smoke I think needed here now...

---

### Post by olsonar on 2006-06-11
try removing

```
/dev/sdb1 /media/sdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
``` 
from your fstab, and then do

```
sudo umount /dev/sdb1
``` 
then

```
sudo nautilus
``` 
navigate to /media/windows, right-click that folder, and under the properties tab, check all the boxes under read (don't do write, since linux doesn't write to ntfs well), then click close. close nautilus, and reboot. it should now work.

---

### Post by karlsson88 on 2006-06-13
I have now solved the problem! 

Thanks for your help everyone!

;)

---

