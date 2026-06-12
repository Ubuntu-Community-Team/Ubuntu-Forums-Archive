---
title: "Kfloppy will not format disks...error"
date: 2008-03-03
forum: Desktop Environments
---

### Post by dbsoundman on 2008-03-03
OK, so I feel like an idiot, because this should be simple, right? I installed kfloppy because I wanted to wipe out some floppies I had laying around, but it doesn't seem to work. I hit Format, press Continue when it warns me, then I get the following message:

Internal Error: Device not correctly defined.

I am not mounting the floppy drive when I try this. I have actually tried it both ways. I even tried putting in /media/floppy0 instead of "Primary" or "Secondary", to no avail. Any suggestions?

Thanks,
Dan

---

### Post by polmir on 2008-03-03
type in terminal
```
cat  /etc/fstab
```
and post output of it

---

### Post by dbsoundman on 2008-03-03
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=e86730c9-6cd4-4740-9fab-49f0c9b9a766 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=5d267503-3e6c-4fb4-9adb-1ed487c83796 /boot           ext3    defaults        0       2
# /dev/hdc2
UUID=e298831a-810b-43da-b490-8727b903bd34 /home           ext3    defaults        0       2
# /dev/hdc1
UUID=2a045458-757f-4594-94da-0dcecec88934 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

Here it is...

-Dan

---

