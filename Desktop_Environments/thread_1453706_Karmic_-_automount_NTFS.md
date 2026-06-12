---
title: "Karmic - automount NTFS"
date: 2010-04-13
forum: Desktop Environments
---

### Post by s-n-ushakov on 2010-04-13
Hi,

I have recently installed Karmic, and everything was fine for while.

I have two NTFS partitions on my drive, and Karmic installer has found them both and made all the arrangements for them. So they were listed in the 'Places' Nautilus menu, and could be easily mounted with a click as '/media/ACER' and '/media/DATA'.

Unfortunately I have destroyed something important by an occasional 'sudo umount /media/DATA' command. Now the 'DATA' resource is still listed in 'Places', but a click at it yields an error message:
```
Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged
```I can still mount 'DATA' with sudo if I create the  '/media/DATA' directory manually. But that's not as cool as it was initially... The other NTFS volume is still mountable with a click as before.

My guess is that the issue is related to some FUSE settings, but I failed to find a right manual...

Any ideas or a push towards some manual would be most appreciated.

Thanks and best regards,
Sergey

---

