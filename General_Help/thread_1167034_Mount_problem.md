---
title: "Mount problem"
date: 2009-05-22
forum: General Help
---

### Post by drdoe on 2009-05-22
So I've got an XFS partition on a seperate drive from my install drive, and today I was fiddling around with the options when you go to properties, basically trying to find out why I didn't have write permissions on it. So under mount options I add rw, prolly a bad idea, seeing as now when I try to mount the drive, it reports that it's unable to mount the media, due presumably to the invalid option specified (rw I'm guessing...), so now I can't find how to get back to the properties of that drive, or change the options back, plus the drive isn't on my fstab table for some reason... any help on the matter would be greatly appreciated, thanks in advance.

---

### Post by drdoe on 2009-05-22
bump, anyone?

---

### Post by x22 on 2009-05-22
suppose the setup is like this:

install drive /dev/sda
second drive /dev/sdb
XFS partition /dev/sdb1

then 

"mount -t XFS -w /dev/sdb1 /<wherever>"

should work: "-w" means "read/write"

---

