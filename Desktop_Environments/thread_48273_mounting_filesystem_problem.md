---
title: "mounting filesystem problem"
date: 2005-07-11
forum: Desktop Environments
---

### Post by yoshic on 2005-07-11
hi guys, how can i mount this filesystem ](*,) , 'fdisk -l' gives me this:

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       20325    10243768+  ef  EFI (FAT-12/16/32)


please help!!!!, 

thanks guys, have a nice day.

---

### Post by jasmuz on 2005-07-11
[QUOTE=yoshic]hi guys, how can i mount this filesystem ](*,) , 'fdisk -l' gives me this:

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       20325    10243768+  ef  EFI (FAT-12/16/32)


please help!!!!, 

thanks guys, have a nice day.[/QUOTE]
 Mounting is as easy as :

sudo mount /dev/hdb1 /mountpoint

---

