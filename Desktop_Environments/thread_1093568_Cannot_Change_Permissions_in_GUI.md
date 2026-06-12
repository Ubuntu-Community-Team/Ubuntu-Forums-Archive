---
title: "Cannot Change Permissions in GUI"
date: 2009-03-11
forum: Desktop Environments
---

### Post by spydamans on 2009-03-11
I am trying to change the permissions of a folder on a mounted usb hdd. When I try to change the permissions in the drop down menu, they change for a second but then change right back to what it was before. Does anyone know how to fix this, any help would greatly be appreciated

---

### Post by taurus on 2009-03-11
What filesystem is your USB harddrive, ntfs or vfat?

```
sudo fdisk -l
df -h
```

---

### Post by spydamans on 2009-03-11
The file system is ntfs

---

