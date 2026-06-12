---
title: "odd fstab problem"
date: 2008-02-10
forum: Desktop Environments
---

### Post by jrd on 2008-02-10
I dont want my windows partition to mount at boot (/dev/hda1)so I added noauto to my fstab.

only problem is that option is being ignored. After reboot the partition mounted by its self.

I know you guys are going to want to see fstab and so on so here it is:

jonathan@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb3
UUID=7b18509c-f211-4a1c-830a-6a32ea0b2966 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=43ab7497-2552-4985-a946-b6fc3e0d8cef /boot           ext3    defaults        0       2
# 
/dev/hda1                           /media/hda1     ntfs                noexec,sync,noauto,user,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=6f9e02a1-6737-4b20-a37e-54b418775840 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Thanks in advance for the help

---

### Post by erfahren on 2008-02-10
I may be wrong about this, but it's worth a try - try changing the mount point to something other than /media and see if that changes anything

---

### Post by jrd on 2008-02-10
I tried your idea...still the same thing though. But /windows is a much better mount point:)

---

### Post by PmDematagoda on 2008-02-10
So why don't you follow the easiest way of doing this and just remove the fstab entry for the WIndows partition?

---

### Post by jrd on 2008-02-10
Lol....well I still want to access it sometimes for music and stuff )that hard drive is bigger so I kep all my music on it) I just dont want it to auto mount. This is very strange..I never had this issue before, noauto normally does the trick.

---

### Post by erfahren on 2008-02-10
this doesn't actually answer your question - but you could remove it from the fstab like PmDematagoda was saying and create a script to mount it when you need it - there's a little guide at  [Hermanzone's site](http://users.bigpond.net.au/hermanzone/p10.htm#Make_a_mounting_script)

---

