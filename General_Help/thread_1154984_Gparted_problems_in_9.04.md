---
title: "Gparted problems in 9.04"
date: 2009-05-10
forum: General Help
---

### Post by Andy06 on 2009-05-10
Gparted is giving me more issues on my 9.04 installs then it did in the previous ones. Specifically, it initially refuses to format external USB drives [must delete existing partitions first] and then forces me to create some sort of MSDOS table (I'm assuming it is deleting the MFT along with the data).
Also getting plenty of "cannot recognise label" errors.

I noticed that you cannot format to NTFS out of the box (have to install ntfs-prog first), was this the case in 8.10 and earlier as well? I never bothered noticing earlier and now all of my installs have been upgraded.

Thanks a lot

---

### Post by agurk on 2009-05-10
I don't know about the USB drive stuff, but yes, ntfsprogs has always been needed in order to format NTFS partitions in GParted.

---

### Post by Andy06 on 2009-05-10
But in the live USB/CD you can format to NTFS out of the box whereas in the full install this out of box functionality does not exist. Is the NTFS-progs package removed during install in the post installation cleanup?

---

### Post by danwood76 on 2009-05-10
With regards to your USB drives I have seen some USB disks that come with no real partition table so one needs to be created before you can format it.

And ntfsprogs might have some copyright issues so isnt included by default but is in the installer so that you can resize windows partitions.

---

### Post by Andy06 on 2009-05-11
Thanks a lot. That resolves all my questions

---

