---
title: "Unable to mount the selected volume."
date: 2005-02-22
forum: Desktop Environments
---

### Post by Chrisb319 on 2005-02-22
That's what it says when I try and read my floppy disk.

> mount: I could not determine the filesystem type, and none was specified

I just used it yesterday.

---

### Post by kcs on 2005-02-23
Is the disk good?

try mount it with the "sudo mount -t vfat -o user,rw /dev/fd0 /media/floppy0" command
or try change in the /etc/fstab the floppy's row

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
>>
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0



i hope this help somthing
Csaba

---

