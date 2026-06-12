---
title: "unionfs with ntfs formated external harddrives?"
date: 2009-01-16
forum: General Help
---

### Post by cugg on 2009-01-16
Hello,
I've a simple question (hopefully...):
I've mounted 3 external harddisks into /mnt/disk(1/2/3). Now I want to merge them (read only) to /mnt/union using unionfs.
I tried [FONT="Courier New"]sudo mount -t unionfs -o dirs=/mnt/disk1=ro:/mnt/disk2=ro:/mnt/disk3=ro unionfs /mnt/union[/FONT]
But here I get an error:
mount: wrong fs type, bad option, bad superblock on unionfs, missing codepage or helper program, or other error.

And here's the point where hopefully someone can help me...

thanks in advance
Rob

---

### Post by cugg on 2009-01-16
Hi,
ok got it to work - somehow it needed to have "/" at the end of the directories.

---

