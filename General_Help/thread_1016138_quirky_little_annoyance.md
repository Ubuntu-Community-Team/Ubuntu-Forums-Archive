---
title: "quirky little annoyance"
date: 2008-12-19
forum: General Help
---

### Post by linuxnoob40 on 2008-12-19
for the longest time now i have an exclamation mark where the update icon would appear and when i click on it i get this error msg

[PHP]Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs[/PHP]

its not a crucial thing as my cdrom drives do work but id like to know why its there and what i can do to get rid of it

---

### Post by Therion on 2008-12-19
Click on: System/Administration/Software Sources.

**UN**check any box you see indicating CDROM.  Be sure to check under the Third Party Software tab too.  

Close and you're done.

---

