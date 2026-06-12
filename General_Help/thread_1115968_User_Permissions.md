---
title: "User Permissions"
date: 2009-04-04
forum: General Help
---

### Post by linux_burner on 2009-04-04
Hi,
This may be sort of silly question, but I don't know how to proceed :)

I created another user account with most privileges except administer the system, config the printer, connect to modem & Monitor system logs. 

I have my music files stored in a different partition (FAT32) and when I try to build collection using Amarok, I get an error saying 'Do not have sufficient permission to access this drive'. What am I doing wrong? What should I enable to obtain access?

Thanks in advance,
-Vishak

---

### Post by taurus on 2009-04-04
How did you mount that fat32/vfat partition?  Did you mount it through /etc/fstab?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

