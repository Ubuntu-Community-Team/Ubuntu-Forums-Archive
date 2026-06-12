---
title: "Gparted crashes on Ubuntu 10.10 with truecrypt"
date: 2011-12-29
forum: Desktop Environments
---

### Post by wearetheborg on 2011-12-29
Gparted crashes on my ubuntu system if there is a truecrypt encrpted USB drive attached, otherwise it runs fine.

With a truecrypt drive attached, it scans the drives, but then dies, without any error messages on the command line.

On attaching another HDD (non-encrypted), it gave the following message on command line (no crash), right after scan.
And the same behavior after reboot.
```
# gparted
======================
libparted : 2.3
======================
Partition(s) 1, 2 on /dev/sdc have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use.  As a result, the old partition(s) will remain in use.  You should reboot now before making further changes.
```

---

