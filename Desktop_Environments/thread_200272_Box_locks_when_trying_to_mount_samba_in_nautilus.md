---
title: "Box locks when trying to mount samba in nautilus"
date: 2006-06-20
forum: Desktop Environments
---

### Post by xadhatter on 2006-06-20
I am trying to mount a samba share as a normal user.  I did chmod +s to smbmnt and can mount shares fine thru a terminal as a norm user. however, when i right click the share in nautilus and try to mount my entire box locks and i have to hard reboot.

/etc/fstab
...
//MCE/Z     /mnt/z     smbfs     noauto,user,guest,rw    0 0

running Ubuntu 6.06... thanks

---

