---
title: "Volume icons disappeared, I can't get it back"
date: 2007-04-01
forum: Desktop Environments
---

### Post by Joe_Bishop on 2007-04-01
I have 3 points in my places menu related to mounted HDD partitions. But after last update they are disappeared. What can I do to return them back?

---

### Post by Die Kuh macht muh on 2007-04-01
Same thing happened to me. Any help would be appreciated.

---

### Post by NikoC on 2007-04-02
In a terminal type: ```
gconf-editor
```
--> apps --> nautilus --> desktop --> make sure the 'volumes-visible' item is checked

---

### Post by y0ssarian on 2007-04-02
open up /etc/fstab in your favorite text editor and change the "default" option on each of the mounted drives to "user"

---

### Post by Joe_Bishop on 2007-04-02
```
/dev/hdb1 /windows/c ntfs-3g silent,umask=0,**user**,locale=ru_RU.utf8 0 0
/dev/hda1 /windows/d ntfs-3g silent,umask=0,**user**,locale=ru_RU.utf8 0 0
/dev/hda2 /windows/e ntfs-3g silent,umask=0,**user**,locale=ru_RU.utf8 0 0

```
Is it the option you mean? A have no volume icons with changed /etc/fstab :(

---

### Post by y0ssarian on 2007-04-02
Yeah thats the option that I was refering to. When I upgraded to feisty my icons dissapeared and that was able to fix it for me. Are the drives mounted in /windows/*? Maybe you can try creating directories in /media and mounting them in there. If that doesn't work, you might try removing 'silent'. Those are my guesses, make sure to back up your file before you try any of that.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3 	/               ext3    defaults,errors=remount-ro 0       1
/dev/sda1	/media/sda1     ntfs    user,nls=utf8,umask=007,gid=46 0       1
/dev/sda4	/media/sda4     vfat    user,utf8,umask=007,gid=46 0       1
/dev/sda2	swap    	sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0      
```

thats my /etc/fstab if it helps.

It might also be an error with ntfs-3g. You might want to check its forums (if it has any) if this doesn't work.

---

### Post by Joe_Bishop on 2007-04-03
I didn't find anything refering to gnome volume icon and ntfs-3g or fuse (ntfs-3g is a superstructure over the fuse). Now I will try "man udev" and related mans. May be, it will help me. :)
Yeah, before this update, my ntfs-3g volumes were mounted to /windows/*, and they were shew in Places menu, so it doesn't matter.

---

### Post by Joe_Bishop on 2007-04-06
I have found this: [https://launchpad.net/ubuntu/+source/hal/+bug/73227](https://launchpad.net/ubuntu/+source/hal/+bug/73227)
So, icons now appears if exececute sudo /etc/init.d/dbus restart

---

