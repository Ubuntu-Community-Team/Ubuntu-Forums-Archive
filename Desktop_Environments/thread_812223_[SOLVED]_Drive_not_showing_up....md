---
title: "[SOLVED] Drive not showing up..."
date: 2008-05-29
forum: Desktop Environments
---

### Post by Barriehie on 2008-05-29
This has been working until today.  Now all of a sudden my drive **hdb1** doesn't show up in nautilus' 'computer' yet I can access it via /home/barrie/disk.  I also had it automounting and putting an icon on the desktop and this also isn't happening.  How can I fix this???

Here is my fstab file.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=eb027411-9ea7-465a-b1a5-0ca148616c8a /               ext3    defaults,errors=remount-ro 0       1
#
# /dev/hda5
UUID=4dab9514-bc4d-0cb3-f605-866524b6795a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#
#    Backup Drive
/dev/hdb1 /home/barrie/disk auto rw,auto,user,exec 0 2
```Many thanks!
Barrie

Okay, I just tried to mount it and machine says only root can do that and it says it's already mounted!  I created a launcher for it and that works but still any ideas as to why I don't get an icon on the desktop??? or why it doesn't show up on my computer???

Thank you for the time!
B.

Now my internet conn. came back up and after I rebooted everything is fine.  I have no clue...
B.

---

