---
title: "palimpsest asking password"
date: 2010-03-26
forum: Desktop Environments
---

### Post by caymahallesi on 2010-03-26
hi

Everytime I try to access my 2nd logical drive I have to enter password. 
How do I remove this password?

user@machine:~$  sudo fdisk -l
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x280a2809

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19122   153597433+  83  Linux
/dev/sda2           19123       30401    90598567+   5  Extended
/dev/sda5           19123       30064    87891583+  83  Linux
/dev/sda6           30065       30401     2706921   82  Linux swap / Solaris

I hope above screen print would help you understand my hdd. 

The drive which is asking for password is : 157gb Ext2
I don't care what type of format it had I choose Ext2 if this type have to ask password I can change it to somethingelse that you recommend. 

thanks

---

