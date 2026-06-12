---
title: "View Mounted Devices"
date: 2004-12-02
forum: Desktop Environments
---

### Post by rikkulinux on 2004-12-02
[FONT=Book Antiqua]How can I view a list of all my mounted devices?  More specifically, I want to print out a detailed list of all the partitions on each of my hard drives and info about them (size, names, file system, etc).  Also, I would like to print out a list of everything I have mounted (hdd, cd-rw, dvd-rw, floppy, usb, etc) and what ubuntu is calling them (hda5, hdb1, etc).

Thanks,
rikku

[/FONT]

---

### Post by p!=f on 2004-12-02
[QUOTE=rikkulinux]How can I view a list of all my mounted devices?  More specifically, I want to print out a detailed list of all the partitions on each of my hard drives and info about them (size, names, file system, etc).  Also, I would like to print out a list of everything I have mounted (hdd, cd-rw, dvd-rw, floppy, usb, etc) and what ubuntu is calling them (hda5, hdb1, etc).

Thanks,
rikku

[/FONT][/QUOTE]
To see what's mounted:
```

mount

```
or
```

cat /etc/mtab

```
To see what should be mounted at boot
```

cat /etc/fstab

```
To see disk usage:
```

df -h

```

There's also a nice graphical utility (Computer -> System Settings -> Disks)

---

### Post by rikkulinux on 2004-12-03
[FONT=Book Antiqua]Thanks.  I'll give them a try.

-rikku
[/FONT]

---

