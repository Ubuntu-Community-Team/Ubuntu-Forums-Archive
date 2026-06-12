---
title: "Mount partition problem"
date: 2009-02-21
forum: General Help
---

### Post by Atzu on 2009-02-21
Hello, as the title says I have a problem mounting partitions... I did not have this problem before... When I try opening the partition I get this error message: Cannot mount volume. You are not privileged to mount the volume 'Partition Name'.
This partition is set up on fstab to automount on startup but it stopped working... Any Ideas??

Thanks in Advance.

EDIT: I have another partition where windows is installed, I can access that partition with no problems.

---

### Post by Atzu on 2009-02-21
Fixed!

what i did was:

```
sudo mkdir /media/Datos 
``` and then ```
 sudo mount -a 
```

and it worked

---

