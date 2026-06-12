---
title: "Mount a NTFS Drive."
date: 2009-05-07
forum: General Help
---

### Post by MatthewpIckering on 2009-05-07
I know this has been posted many times before but I have failed to get it to work.

```
fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33f86417

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30402   244196352    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
```

---

### Post by colau on 2009-05-07
It may help.
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

---

### Post by sjuranic on 2009-05-07
"mount -t ntfs" doesn't do it for you?  What have you tried so far?

---

### Post by MatthewpIckering on 2009-05-07
Sorted with,  mount -t ntfs-3g /dev/sda1 /media/ -o force

Thank!

---

