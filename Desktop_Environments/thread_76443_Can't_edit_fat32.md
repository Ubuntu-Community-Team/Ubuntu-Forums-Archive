---
title: "Can't edit fat32"
date: 2005-10-15
forum: Desktop Environments
---

### Post by unixsphere on 2005-10-15
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda5       /media/hda5     vfat    defaults,users        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

This is my /etc/fstab file, how do I make it so that I can edit my fat32 which is on /dev/hda5 ?

---

### Post by manicka on 2005-10-15
I use this type of fstab to make fat32 writeable

/dev/hda9      /media/music          vfat     defaults,rw,umask=000 0 0

---

### Post by The Waco Kidd on 2005-10-15
[QUOTE=unixsphere]```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda5       /media/hda5     vfat    defaults,users        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

This is my /etc/fstab file, how do I make it so that I can edit my fat32 which is on /dev/hda5 ?[/QUOTE]

You need to change the line refering to the vfat partition so it looks something like this:

```

/dev/hda /media/hda5 vfat uid=1000,gid=1000 0 0

```

Where uid=1000 and gid=1000 are the numeric system IDs for the user and default group the user belongs to. If you are using the account created when your installed Ubuntu the IDs in your system they will be the same. With this setup I can read and write files to the FAT32 partiton without a problem.

Credit where it's due, I've copied and pasted this solution almost verbatim from the one which was given to me a week ago in [this thread]("http://www.ubuntuforums.org/showthread.php?t=70777"). It works!

---

### Post by GTvulse on 2005-10-15
Don't forget to add utf8 to the options line, or you'll have filename corruption if using accented characters. :-)

---

### Post by unixsphere on 2005-10-16
[QUOTE=dradul]Don't forget to add utf8 to the options line, or you'll have filename corruption if using accented characters. :-)[/QUOTE]

So what should it look like exactly? I dont want to mess it up even though its all backed up.

---

### Post by GTvulse on 2005-10-16
[QUOTE=unixsphere]So what should it look like exactly? I dont want to mess it up even though its all backed up.[/QUOTE]
```
/dev/hda /media/hda5 vfat utf8,uid=1000,gid=1000 0 0
```

will work. :-)

EDIT: To anyone reading this thread after the fact. We need to use utf8 converson on the Linux side to be compatible with WIndows 2000/XP/2003/Vista (namely, Windows NT 5.x), because those OSs use Unicode internally in **all**  filesystems (NTFS, FAT32) supported for OS installation.

---

