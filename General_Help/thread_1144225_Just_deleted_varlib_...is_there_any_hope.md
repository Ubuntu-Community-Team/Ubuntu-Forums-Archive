---
title: "Just deleted /var/lib ...is there any hope?"
date: 2009-04-30
forum: General Help
---

### Post by supergrover1981 on 2009-04-30
Hi gang,

Erm...In a moment of monumental stupidity, I just deleted /var/lib (recursively). In short, is there any hope of recovery from this?

I still have access to the command line. Intermediate-ish level user...(or so I thought until I was stupid enough to delete /var/lib)

Cheers,
       - SuperGrover

---

### Post by Polygon on 2009-04-30
....not really =P you would have to copy the fles from another installation, but then things would go wrong, files that are there wont still be there, it really is just easier to buy/borrow a external hard drive and mount it:

sudo fdisk -l (to get the /dev/ location of the drive)

sudo mkdir /media/<mount directory>

sudo mount /dev/sda# -t <filesystem here, vfat, ext3, etc> /media/<mount directory>

and then cp your entire home folder and whatever else you want to save, then reinstall. and be more careful about deleting stuff =P

---

