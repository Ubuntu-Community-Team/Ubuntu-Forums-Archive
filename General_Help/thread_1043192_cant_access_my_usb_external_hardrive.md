---
title: "cant access my usb external hardrive"
date: 2009-01-18
forum: General Help
---

### Post by kapi on 2009-01-18
hi there,

dont seem to be able to mount the usb hard disk drive that was working on vista. have moved to Ubuntu and the thing wont mount. 

Could some one please advice, would be very grateful

thanks

Kapi

---

### Post by scouser73 on 2009-01-18
Did you recently have it plugged into a Windows PC, if so you'll need to stick it back into the Windows PC then use the **Safely Remove Hardware** function.

---

### Post by cdtech on 2009-01-18
Open a terminal and type:
```
sudo fdisk -l
```
See if it is showing in the list.

**UPDATE::.**
You can repair an NTFS journal by installing "ntfsprogs" and doing an "ntfsfix" on the device using Linux..........

---

