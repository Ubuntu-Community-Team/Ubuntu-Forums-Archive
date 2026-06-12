---
title: "Startup error"
date: 2006-09-27
forum: Desktop Environments
---

### Post by Magiczero on 2006-09-27
Hi  When I start my computer I get this thing that says an error on your filesystem has occoured please repair manually

can anyone help here please?

Thanks

---

### Post by Magiczero on 2006-09-27
here is my etc/fstab file incase you need that

>     # /etc/fstab: static file system information.
    #
    # <file system> <mount point> <type> <options> <dump> <pass>
    proc /proc proc defaults 0 0
    /dev/hda1 / ext3 defaults,errors=remount-ro 0 1

    /dev/hdb1 /foo ext3 defaults,errors=remount-ro 0 2 


/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

/dev/hdb1       /media/hdb1     ext3    nodev,nosuid        0       2


---

