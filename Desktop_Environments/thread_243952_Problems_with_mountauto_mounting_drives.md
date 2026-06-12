---
title: "Problems with mount/auto mounting drives"
date: 2006-08-25
forum: Desktop Environments
---

### Post by dude051 on 2006-08-25
I know this has been discussed quite a bit here, but I still am having problems and can not fix my issues, which are...

I have an Acer laptop running Dapper 6.06 LTS, recent 686 SMP kernel. My fstab was:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /boot           ext3    defaults        0       2
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

What I want, is my two vfat partitions to auto mount and link on my Desktop and in Computer. First off though, Nautilus reconizes these partitions and places them in Computer as Acer and AcerData (their drive labels). But they are not mounted and just error with
```

Unable to Mount the selected volume:

error: device /dev/sda3 is not removable
error: could not execute pmount
```

Reading through some post here, I saw some solved it by creating hdaX in the media folder and mounting the device there. This didnt work, so instead I made /media/sda2 and mounted /dev/sda2 to it. Now when I access from Computer, the Acer link doesnt error, but does nothing at all. Eh?

Ok, so after a restart of gnome, Nautilus removed the Acer link and now /dev/sda2 is auto mounted to /media/sda2. No link on the Desktop or Computer... but I can access the drive through /media/sda2!

So since that didnt work, I removed the /media/sda2, restarted gnome and all was back to the way it was. Then created /media/C and /media/D and added the devices to auto mount in fstab.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /boot           ext3    defaults        0       2
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

# Windows Drive Mounts
/dev/sda2      /media/C        vfat    defaults,auto,user        0       0
/dev/sda3      /media/D        vfat    defaults,auto,user        0       0
```

This doesn't work either, now I get no links on my Desktop or Computer and Nautilus took away both Acer and AcerData icons (well they didnt work anyways..).. but I can access them by going to /media/C and /D..

Its driving me crazy, I dont know why they arent being picked up in Nautilus or the Desktop. I know I could eaisly mount them to the Desktop and/or create Bookmarks in Nautilus... but its not the same :twisted: Plus the principal that this isnt working gets at me. Any help is appreciated!

---

### Post by dude051 on 2006-08-25
Bump, no one?

---

