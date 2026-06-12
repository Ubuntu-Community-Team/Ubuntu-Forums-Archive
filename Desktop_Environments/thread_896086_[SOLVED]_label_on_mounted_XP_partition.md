---
title: "[SOLVED] label on mounted XP partition"
date: 2008-08-20
forum: Desktop Environments
---

### Post by neill on 2008-08-20
hi

i dual boot hardy and XP, but use hardy for everything except gaming

the XP partition (c: effectively) is mounted on the desktop and the /etc/fstab entry is as follows

```
#Entry for /dev/sda1 :
UUID=503432B1343299C4	/media/disk	ntfs-3g	defaults,nosuid,nodev,uhelper=hal,locale=en_GB.UTF-8	0	0
```

the desktop label for that partition is 187.4GB Media

how can i change that label ?

thanks

/neill

---

### Post by S.A.A on 2008-08-21
Read this [https://help.ubuntu.com/community/RenameUSBDrive?highlight=%28CategoryUsb%29](https://help.ubuntu.com/community/RenameUSBDrive?highlight=%28CategoryUsb%29)

---

### Post by neill on 2008-08-21
Perfect - thank you

/neill

---

### Post by neill on 2008-08-21
OK that didn't work - followed it exactly but to no avail

```
neill@ubuntu-desktop:~$ sudo umount /dev/sda1
neill@ubuntu-desktop:~$ sudo ntfslabel /dev/sda1
xp
neill@ubuntu-desktop:~$ sudo mount /dev/sda1
```

but on the desktop and in nautilus it's still labelled as 187.4GB media

again the fstab entry now reads

```
# Entry for /dev/sda1 :
UUID=503432B1343299C4 /media/xp ntfs-3g defaults,nosuid,nodev,uhelper=hal,locale=en_GB.UTF-8 0 0
```

any further thoughts ?

/neill

---

### Post by neill on 2008-08-21
fixed it - or rather worked round it

used gconf to hide the partitions then configured launchers as i needed

:)

---

