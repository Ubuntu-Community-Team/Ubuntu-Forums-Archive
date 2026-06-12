---
title: "Waiting for root filesystem..."
date: 2006-06-28
forum: Desktop Environments
---

### Post by Sean-Michael on 2006-06-28
I just installed my external drive, "WD 250gb" drive into my machine because I have no need at this point to use it externally and hate turning it on just for music and other stuff.

So it bolts right up and mounts right into my WindowsXP boot "Dual Booting" but when I goto boot my beloved Ubuntu os I get this far...

```
Loading Essential Drivers :                 [OK]
Mounting Root File System :                blank
Waiting for root filesystem :              blank
```

And I dont know what to do, is this something I can fix with my live CD?  I mean is this a grub loading problem or is it in the fstab?
I am new to linux but I'm learning my way around... :lol: 

Anxiously waiting for help, Thanks!

---

### Post by yage on 2006-06-28
Sounds like both... grub and fstab

---

### Post by Sean-Michael on 2006-06-28
lol, yea, thats what I was thinking, due to the new drive, I think my partitions might be re named but I need to fix it and Im a lil lost as to where to start,  using the search feature I find a few hits but alot of the issues seem to be pointed at a usb installation but my system was contained to my primary drive... only data files are on my external drive, now internal... sigh... I dont know where to start.

---

### Post by Sean-Michael on 2006-06-28
Ok, so I had an old fstab saved and I have confirmed that that what was once hd_a_1 is now hd_b_1 so when booting my system is looking in the new drive for the filesystem where it thinks it is at when its actually been re named but how the heck do I fix this?

Please someone help me lol!

---

### Post by Patrick-Ruff on 2006-06-28
without grub this could be an issue, because within grub you could merely select the partition you want to boot up with, then hit 'e' then find the line that states your hard drive, then hit 'e' again, then change the drive names corectly. it would be something like root=/dev/hard drive name  etc. 


then you would exit out of that line after you edited it, you would select hte line you edited, and hit 'b' then after you log on, you have to edit the fstab file to make the changes stick


good luck

---

### Post by Sean-Michael on 2006-06-28
Awesome, I'm back into linux now!:D 
I'm hoping I can get more help, here's what my fstab looks like;

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       /media/hda3     ext3    defaults        0       2
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Do I simply change all the hda entries to hdbs?  Like this;

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb3       /media/hdb3     ext3    defaults        0       2
/dev/hdb5       /media/hdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

and do I need to do anything other operations or simply save and reboot?

Thankyou very much for your help Patrick-Ruff!

---

### Post by Sean-Michael on 2006-06-29
Well, I've got my fstab back into order but I'm a little cunfused with grub, but I think with some more research I can get threw it, looks simple enough but that can be a miss judgment I guess,  I'd hate to screw it up lol

Thanks!

---

### Post by davescafe on 2006-07-09
> **Sean-Michael said:**
> Well, I've got my fstab back into order but I'm a little cunfused with grub, but I think with some more research I can get threw it, looks simple enough but that can be a miss judgment I guess,  I'd hate to screw it up lol

Thanks!

Hi Sean-Michael;

I have posted some steps in another thread that should help you resolve this problem:

[http://www.ubuntuforums.org/showpost.php?p=1231460&postcount=62](http://www.ubuntuforums.org/showpost.php?p=1231460&postcount=62)

Dave

---

