---
title: "1420N DVD drive not reading disks (resolved)"
date: 2007-07-24
forum: Dell  Ubuntu Support
---

### Post by Shay Stephens on 2007-07-24
The DVD drive was not reading cd's or dvd's, it gave a message that it couldn't mount /dev/scd0 so I checked the hardware information app and it listed the dvd drive under hda, so I changed the /etc/fstab file to use /dev/hda0 instead of /dev/scd0 and saved and rebooted.  As soon as I was rebooted I could read cd's and dvd's :-)

Hope that helps someone out there.  Here is a list of my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6e61e402-f5c5-4777-a2da-f8374bc05ec7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=29c7ae5e-3c5b-4a55-8ac3-b2c8bbf2def4 none            swap    sw              0       0
/dev/hda0       /media/cdrom0   udf,iso9660 user,noauto     0       0
UUID=a95aa336-8598-4fba-a597-bd0846e1e61a  /boot ext3 defaults 0 0
```

Here is the relevant part:
```
/dev/hda0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

