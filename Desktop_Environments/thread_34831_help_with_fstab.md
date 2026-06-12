---
title: "help with fstab"
date: 2005-05-16
forum: Desktop Environments
---

### Post by neighborlee on 2005-05-16
I am wondering about  /media/DriveE in that it is in fstab and I can browse to it in the filesystem..but its not showing up in nautilus when I launch it via: Places :computer..can someone help me diagnose why this is so ? ;-)

btw here is my fstab line:

/dev/hda5       /media/DriveE   ntfs    ro,umask=000 0   0


cheers
neighborlee

---

### Post by joncooper on 2005-05-16
FWIW, here's the entry for my ntfs partition that happily shows up in Computer and Places:

/dev/sda1	/mnt/datadrive	ntfs	auto,ro,user,gid=100,umask=0007	0	0

---

### Post by neighborlee on 2005-05-16
[QUOTE=joncooper]FWIW, here's the entry for my ntfs partition that happily shows up in Computer and Places:

/dev/sda1	/mnt/datadrive	ntfs	auto,ro,user,gid=100,umask=0007	0	0[/QUOTE]
--------------
okay thx that did it..I wonder if ubuntu team is planning on making this a permanant fix to avoid having to do this manually ( similar to xandros,mdk I think)

cheers
neighborlee

---

