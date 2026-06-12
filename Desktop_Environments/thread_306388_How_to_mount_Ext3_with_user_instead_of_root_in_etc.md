---
title: "How to mount Ext3 with user instead of root in /etc/fstab"
date: 2006-11-24
forum: Desktop Environments
---

### Post by ryurhrt on 2006-11-24
Hey, my problem is clear, when i just start up, the partition which is in Ext3 File system is mount with root, i cannot copy file inside...

This i small problem, then i just simply chmod 777 to that mount point. After copy my file inside, i can access to that folder, and even add files. However, after some while, i found the problem. when I delete file, the file doesn't go to trash 1st, i afraid if i wrongly deleted something...

ok then i chown and chgrp the mount point, problem solve, but is there any way to set in /etc/fstab to mount the partition by user, and not root.

Thanks for helping :)

---

### Post by taurus on 2006-11-24
Usually, you use the chmod or chgrp to set up permissions with ext3 filesystem.  And yes, once you delete something, it's gone so that's why you need to be careful what directory you set the permissions to.  

Meanwhile, let's have a look at your /etc/fstab then!

Applications -> Accessories -> Terminal:

```
cat /etc/fstab
```

---

### Post by ryurhrt on 2006-11-24
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=a1915bb1-f322-410c-86bd-6f994a6d932e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=EA5CDD315CDCF971 /media/C        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=84185BD8185BC836 /media/E        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdd5
/dev/hdd5  /media/F        vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sda6
UUID=2ba8d832-a93d-471d-ac18-0f6afbe7871e /media/MyStore  ext3    defaults        0       2
# /dev/sda3
UUID=ce71fc7a-6f1f-4040-b21f-d6985f3b6a80 /media/suse     ext3    defaults        0       2
# /dev/sda5
UUID=aa508b94-2df8-4ba8-9c22-5035f0809e3a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0



The problem is at the MyStore there !! i want use it to store my data.

---

### Post by aysiu on 2006-11-24
Try pasting these commands in the terminal: ```
sudo chown -R ryurhrt:ryurhrt /media/MyStore
sudo chmod -R 755 /media/MyStore
``` Substitute in your actual username if it's not ryurhrt.

---

### Post by taurus on 2006-11-24
If you want to use /media/MyStore to store your data, then why not give permissions to everybody because that's probably the easiest way to go.  If you accidentally remove something in there that you are not supposed to, it will not crash your system...  

```
sudo chmod 777 /media/MyStore
```

---

### Post by tomcheng76 on 2006-11-24
use the flag "user,noauto" allow you to let normal user to mount and umnout that partitation. just put the mount command into the startup script. Then it is fine.

---

### Post by ryurhrt on 2006-11-24
Thanks..., but after i restart, is that /media/MyStore still belong to ryurhrt and not root?

and for the chmod 777, will it also>

---

### Post by taurus on 2006-11-24
aysiu's method is what you want if you want to be the owner of /media/MyStore.

---

### Post by aysiu on 2006-11-24
You need to do ```
sudo chmod **-R** 777 /media/MyStore
``` if you want the subfolders and files to all have read/write/execute permissions for everyone. The *-R* flag makes the permission changes recursive. Otherwise, it affects only the top-level folder.

And, yes, those changes will stay even after a reboot.

---

### Post by ryurhrt on 2006-11-24
yeah thanks for helping... i learn a lot here :)

---

### Post by SuperAndy on 2007-10-06
i have followed aysiu's instructions, and i do now have an ext3 volume that is read-writeable without sudo.

however, how do i give this volume a .trashes folder, and how do I make deleted things move to this folder before they vanish totally?

---

