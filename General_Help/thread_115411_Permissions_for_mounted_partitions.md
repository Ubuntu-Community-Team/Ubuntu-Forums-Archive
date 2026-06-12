---
title: "Permissions for mounted partitions"
date: 2006-01-10
forum: General Help
---

### Post by tonyisntcreative on 2006-01-10
At the moment I'm using a dual boot setup with Windows 2000 and Ubuntu 5.10.  I have two shared FAT32 partitions (hda5 and hda6).  The partitions are mounted in Linux and I'm able to "read" the files, but that's it.  

I've tried everything I could think of (I am really new to this, though) to change the permissions of the two partitions so I can read, write, etc. to these partitions.  I've tried chmod 777 and it didn't do anything.  I've tried editing the options in my fstab file...nothing.  By this point I'm clueless.  

I want to have these partitions open to anything so I can download music into them using Nicotine (currently it says "local file error" when I have a folder on hda5 set as my shared folder) and also so I can use Rythmbox to play my music (it currently plays in only Totem, and for some reason skips....but on my other hard drive Rythmbox worked, but I still had the other permission problems.)

So...PLEASE, if  you can, help me make these partions free!

---

### Post by Robgould on 2006-01-10
You need to edit your fstab to specify userid and groupid.  Both are 1000.

---

### Post by tonyisntcreative on 2006-01-10
Okay, so how should that look?  This is my current fstab (I changed everything back to default)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by aysiu on 2006-01-10
[QUOTE=tonyisntcreative]Okay, so how should that look?  This is my current fstab (I changed everything back to default)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```[/QUOTE] First, I'd issue these commands: ```
sudo cp /etc/fstab /etc/fstab_backup
sudo umount /media/hda5
sudo umount /media/hda6
``` You might try using different mount points, though. I think the /media folder can be a bit buggy sometimes because that's where the USB devices get hotplugged to, and there's too much special automatic stuff happening there.

I'd try ```
sudo mkdir /fat_drive_1
sudo mkdir /fat_drive_2
``` Then change those /etc/fstab lines to ```
/dev/hda5       /fat_drive_1     vfat    iocharset=utf8,umask=000        0       0
/dev/hda6       /fat_drive_2     vfat    iocharset=utf8,umask=000        0       0
``` Then ```
sudo mount -a
```

---

### Post by tonyisntcreative on 2006-01-10
Everything is working now.  Thank you for the help!

---

