---
title: "Lost Disk and trying to repair without reinstalling"
date: 2008-12-30
forum: General Help
---

### Post by takeawaydave on 2008-12-30
I lost a disk this weekend which had /var mounted on it,

The machine is very old and does not have a cdrom drive. Otherwise I would reinstall.

I need to try and get apt working again.

Currently getting:

```
root@denali:~# apt-get remove apache2
E: Could not open lock file /var/lib/dpkg/lock - open (2 No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
root@denali:~# 
```

I tried reinstalling apt as per [HTML]http://ubuntuforums.org/archive/index.php/t-77658.html[/HTML]:

```
wget http://archive.ubuntulinux.org/ubuntu/pool/main/a/apt/apt_0.7.14ubuntu6_i386.deb
root@denali:~# dpkg -i apt_0.7.14ubuntu6_i386.deb
``` 

but get
```

dpkg: unable to access dpkg status area: No such file or directory
```

---

### Post by Woody1987 on 2008-12-30
whats the output from ```
sudo fdisk -l
```

---

### Post by takeawaydave on 2008-12-30
root@denali:~# fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          12       96358+  83  Linux
/dev/hda2              13        4255    34081897+  83  Linux
/dev/hda3            4256        4754     4008217+  83  Linux
/dev/hda4            4755        9729    39961687+   5  Extended
/dev/hda5            4755        9500    38122213+  83  Linux
/dev/hda6            9501        9729     1839411   82  Linux swap / Solaris
root@denali:~#

---

### Post by takeawaydave on 2008-12-30
I have copied over from another ubuntu installation.

Its not the correct version though (8.04 rather than 7.04).

Any one suggest on how I can proceed?

---

