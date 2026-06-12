---
title: "Just edited fstab, can someone check i've got it right?"
date: 2009-05-04
forum: General Help
---

### Post by boyofford on 2009-05-04
Hi just edited my fstab so that a internal partition mounts at startup, seems to be working but was unsure of options so just copied from root, does this look right?
> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=3a316bb2-365f-4e2c-a34b-90c1626aff5b /               ext4    **relatime,errors=remount-ro 0  **     1
# /home was on /dev/sda7 during installation
UUID=ca78f269-0a4a-4735-b99f-cf20e6922239 /home           ext4    relatime        0       2
# swap was on /dev/sda6 during installation
LABEL=swap      none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
LABEL=files    /media/files   ext3 **defaults,errors=remount-ro ** 0

The partition is labeled files, and the bold is what i copied and where i copied it to.
Must admit didn't really understand it, but seems to be working.
Will this give me any problems?:confused:

Thanks in advance

---

### Post by version7x on 2009-05-04
Your entry looks fine.

A bit on the bolded options...

The defaults bit sets default mount options.  They are:

```
Use  default  options:  rw,  suid,  dev, exec, auto, nouser, and async.
```

For more information on mounting options look at the man page for "mount."

The errors=remount-ro option is how the mount command is going to handle errors.  In this case, it will remount the device read only.

There's great information about all of the fields in the man pages for both mount and fstab.

Hope that helps!

---

### Post by boyofford on 2009-05-05
> **version7x said:**
> Your entry looks fine.


Thanks, I did try and read about the options but didn't fully understand them

I've only just got past the newbie cut and paste use of the terminal!:lolflag:

All seems well, but I'll have another read of the documentation, i'd like to understand what i did exactly.

---

### Post by dcstar on 2009-05-05
> **boyofford said:**
> Hi just edited my fstab so that a internal partition mounts at startup, seems to be working but was unsure of options so just copied from root, does this look right?


The partition is labeled files, and the bold is what i copied and where i copied it to.
Must admit didn't really understand it, but seems to be working.
Will this give me any problems?:confused:

Thanks in advance

The /media folder is for automatically mounted filesystems, not permanent ones.

Create a separate mount point with:
```

sudo mkdir /myfiles-whatever
```

and use that, do not use system folders for your own stuff.

---

### Post by boyofford on 2009-05-05
> **dcstar said:**
> The /media folder is for automatically mounted filesystems, not permanent ones.

Create a separate mount point with:
```

sudo mkdir /myfiles-whatever
```

and use that, do not use system folders for your own stuff.

oh, that makes sense, i'll change it when i get home.

---

