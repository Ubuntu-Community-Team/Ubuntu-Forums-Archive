---
title: "Could not mount device"
date: 2005-03-25
forum: Desktop Environments
---

### Post by niti on 2005-03-25
I could not enter my other partitions and hdd in KDE 3.4 in kubuntu. It gives me error in media directory. I see the following error.

Could not mount device.
The reported error was:
mount: can't find /dev/hdb1 in /etc/fstab or /etc/mtab

What should I do? Thanks...

---

### Post by digby on 2005-03-25
What command did you use in your attempt to mount them?  Is hdb an optical drive of some sort?

---

### Post by wbeck85 on 2005-03-25
[QUOTE=digby]What command did you use in your attempt to mount them?  Is hdb an optical drive of some sort?[/QUOTE]
 If "hdb" is an optical drive, try mounting "/dev/cdrom" or something like that.

---

### Post by bailout on 2005-03-26
Try here [http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

gedit is not installed on kubuntu so you will have to use another editor. Unfortunately kate crashes when trying to open as sudo so I ended up using nano.

---

### Post by niti on 2005-03-26
hdb is my other hard disk with 250GB.

---

### Post by digby on 2005-03-26
It would still help to know what you've tried.  The proper way would be something like

```
#mkdir /mnt/location
#mount /dev/hdb /mnt/location -t auto
```

Replace /mnt/location with wherever you want your drive mounted.

---

