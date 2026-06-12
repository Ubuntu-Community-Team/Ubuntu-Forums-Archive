---
title: "Ghost files only in windows folder....."
date: 2005-02-01
forum: Desktop Environments
---

### Post by paulo on 2005-02-01
Firstly, thanks again for all your help babysitting the newbie.

 I REALLY need to get access to my windows files from Linux and still cant get it working. I have edited Fstab, and I now have a windows folder in mnt and have mounted my windows drive to it. When I open this folder all the files are there - I recognise the names - but they all have the same icon (a footprint) and register 0 bytes. They do not open when left clicked and dissapear if right clicked.
 :?: 
So I have reached the drive, but not the files. Any ideas?
Thanks,
Paulo

---

### Post by Buffalo Soldier on 2005-02-01
What's your fstab content?

---

### Post by paulo on 2005-02-01
Hers my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/windows auto unmask=0222 0 0
/dev/hda1 /mnt/windows auto defaults 0 0

Ideas?

---

### Post by valadil on 2005-02-01
Actually I do have an idea.  You should only be mounting hda1 once.  Get rid of one of them.  Also, unmask should be umask.

---

### Post by paulo on 2005-02-01
YeeeeeeHAH!

Cracked it.
Windows directory now working fine. I think I figured out the problem: I was putting single spaces in between the parts of the commands, not hitting the TAB key. When I did this and restarted, it worked. That and changing unmask to umask.

fstab now looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/hdb5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda1 /mnt/windows auto umask=0222 0 0

Many thanks to y`all who posted, particularly Valadil.
Now I can get on with learning my command lines whilest listening to some decent tunes: "write one hundred times: /dev/hda1 /mnt/windows auto UMASK=0222 0 0"

Thanks very much,
Paulo

---

