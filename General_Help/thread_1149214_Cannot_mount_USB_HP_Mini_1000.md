---
title: "Cannot mount USB HP Mini 1000"
date: 2009-05-05
forum: General Help
---

### Post by Jonothewright on 2009-05-05
I just recently got an HP Mini 1000 (MIE edition) and installed Ubuntu 8.04 on it. Everything works great except that I cannot mount USB thumb drives or SD cards. Whenever I insert one I get this message:

"Cannot mount volume. Invalid mount option when attempting to mount the volume."

I know that it isn't a problem with the USB ports since I just reinstalled the system from a USB thumbrive. Maybe it is a wierd fstab problem, but I am not extremely knowloedgable with fstab. Here is what the file looks like if it might help:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3f582e23-6762-442c-8aff-1db8dd675cfe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ac9357a2-6d6b-4e02-aedc-496f8f2a2b53 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

A big thank you in advance to anyone who even takes the time to look over this.

Cheers
Jonathan

---

### Post by stretch427 on 2009-05-05
Well I would tend to agree that its not a hardware problem because you were able to install. Have you tried changing permissions to mount? 
```
Places -> Computer -> Properties(of said Drive) -> Volume
```

It'll show you a mount point, and insert that mount point into this command
```
nano /etc/fstab /dev/(your_mount_point)
```

And post the output of that here and then maybe I can see a little of what's happening.

---

### Post by Jonothewright on 2009-05-07
Thank you for the reply.

I tried looking at the volume under Places>Computer but it doesn't have a "volume" tab in the preferences for this device. It does state under the basic information that the volume is unknown. Under the permissions tab it states that the permissions cannot be determined. It does the same thing for SD cards that I insert.

I don't know what to make of this, so thank you again for all the help.

Cheers
Jon

---

