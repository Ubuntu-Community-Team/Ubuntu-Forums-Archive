---
title: "no automounting CDrom"
date: 2009-02-12
forum: Desktop Environments
---

### Post by kimyoungil on 2009-02-12
Hello guys,
I've got a problem with mounting CDroms.
I can mount them with the console, using 
mount /media/cdrom 
it works perfectly then.

But when i put a new CD in the drive, it doesn't recognise the CD, like it did a month ago. If i use the filebrowser to mount it I get a message saying something like "couldn't mount location, can't mount file" (in dutch). I can unmount drives this way, but i can't mount them. And using the console everytime isnt fun.

```

My fstab looks like this: (after a lot of changes)
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                    0  0  
/dev/sdb5
UUID=48c506d4-42ad-4797-9121-ad6f9ecb406d  /                ext3         relatime,errors=remount-ro  0  1  
/dev/sdb6
UUID=32c28ebf-b25e-461f-9885-261a83cde8c5  none             swap         sw                          0  0  
/dev/scd0  /media/cdrom1    auto    ro,user,noauto,utf8    0  0
/dev/cdrw1 /media/cdrom0    auto    ro,user,noauto,utf8    0  0
/dev/sda1                                  /media/winXP     ntfs         defaults                    0  0  
/dev/sda2                                  /media/FAT       vfat         defaults                    0  0  
/dev/sda3                                  /media/programs  ntfs         defaults                    0  0  
/dev/sdb1                                  /media/sdb1      vfat         defaults                    0  0  
/dev/sdb2                                  /media/shared    ntfs         defaults                    0  0  

```


I've already looked around a bit at the forums, and foutn this post: [http://ubuntuforums.org/showthread.php?t=1038389&page=3&highlight=cannot+mount+file+cdrom](http://ubuntuforums.org/showthread.php?t=1038389&page=3&highlight=cannot+mount+file+cdrom)
After trying everything there i don't have to sudo mount, but i can just use mount. But the real problem stays.

---

### Post by kimyoungil on 2009-02-12
well, i've tried some more. I've looked at the lschal log. This is what is says when inserting a disk:

```

22:56:27.024: storage_model_DVD_RW_ND_3540A property storage.removable.media_available = true
22:56:27.071: storage_model_DVD_RW_ND_3540A property storage.cdrom.write_speeds = {'8467', '7056', '5645', '4234', '2822', '1411'}
22:56:32.949: volume_label_SS20AE added

```
so it reads the disk, but there is something wrong when it tries to mount.

when i mount it from console it says this:
```

22:58:08.873: volume_label_SS20AE property volume.mount_point = '/media/cdrom0'
22:58:08.878: volume_label_SS20AE property volume.is_mounted_read_only = true
22:58:08.882: volume_label_SS20AE property volume.is_mounted = true

```
so these last steps aren't done when inserting the disk. Only when mounting from console it works. I hope this helps.


edit: the cds are automatically displayed in /dev/disk/by-label
so that's the point where it stops.

---

### Post by kimyoungil on 2009-02-15
Just a bump.
If noone knows, i'll give up...

---

