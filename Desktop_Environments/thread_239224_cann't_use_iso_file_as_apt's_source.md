---
title: "cann't use iso file as apt's source"
date: 2006-08-18
forum: Desktop Environments
---

### Post by zjcim on 2006-08-18
i got a xubuntu iso and install a server with this iso

wo want to setup a X desktop 

After  i mount -o loop /path/xubuntu.iso /media/cdrom
,apt-get install a software ,systmen tells :eject - ejects CDs and operates CD-Changers under linuxdebian

what's up??

thx

---

### Post by Jagot on 2006-08-19
With the CD in the drive, try running this command instead:

```
sudo apt-cdrom add
```

---

