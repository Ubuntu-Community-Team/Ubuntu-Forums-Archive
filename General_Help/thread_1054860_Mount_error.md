---
title: "Mount error"
date: 2009-01-30
forum: General Help
---

### Post by wirewrangler on 2009-01-30
I messed up badly. I thought I knew what I was doing. I added /media/ as the mount point in the properties window of a logical volume. now none of my other partitions will mount. I tried formating, I even tried deleting the logical volume, resizing the partition, still to no avail. What can I do?

---

### Post by Thanoulis on 2009-01-30
Can you post the output of:
```
cat /etc/fstab
```

---

### Post by wirewrangler on 2009-01-30
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=62d81330-4dda-402c-aa26-abbaf5b28e85 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=942b4a81-04b8-4318-83ca-2d544f5551e5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=1003,devmode=664 0 0

---

### Post by blazemore on 2009-01-30
None of your "other" partitions are even listed.
What partitions do you have?

---

### Post by wirewrangler on 2009-01-30
sda4 is a primary partition that has a kalyway installation on it. Sda5 is an extended partition with logical volume sda6 that originally was formatted NTFS for a virtulbox windows 2000 installation. the last line of the fstab has to do with steps taken in order to make my nokia work with pc suite in windows under virtual box. I thought, most unfortunately, that the mount point portion of properties was a gui path to making it auto mount on boot.

---

### Post by blazemore on 2009-01-30
Add lines to your /etc/fstab
```
sudo gedit /etc/fstab
```

Add them in the following format:
```
devicename mountpoint filesystem options 0 0
```

For example,
```
/dev/sda6 /win2000 ntfs defaults 0 0
```
You'll have to make the mountpoints first.

```
sudo mkdir /win2000 for example
```

---

