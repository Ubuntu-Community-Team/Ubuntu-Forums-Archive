---
title: "Update problems"
date: 2009-03-24
forum: General Help
---

### Post by Yususf on 2009-03-24
Hi There

I am having a problem when doing updates the following is displayed.ardy Heron_ - 

Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Please advise what to do

---

### Post by blazemore on 2009-03-24
Do you get this when you do ```
sudo apt-get update
```
Is it actually preventing you from upgrading your system?

This error is just because of a cdrom, it doesn't actually affect upgrades.

Please post the output of
```
cat /etc/apt/sources.list
```

---

### Post by Yususf on 2009-03-24
It does not install the update.

---

### Post by blazemore on 2009-03-24
Please post the output of
```
cat /etc/apt/sources.list
```

---

