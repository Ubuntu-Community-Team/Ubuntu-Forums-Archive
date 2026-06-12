---
title: "How is a 2nd/USB hard drive handled in FHS?"
date: 2009-03-04
forum: General Help
---

### Post by Firestem4 on 2009-03-04
I'm curious to know how a 2nd hard drive or USB/external HDD is handled in the Unix-Filesystem Hierarchy Standard. 

My experience with computers is 99% Windows (1% Linux lol) So I am used to Directories. But as /root is where all files literally branch out from, I don't know how the mounting works. Are they loaded on /media or elsewhere?

Thanks in advance!

---

### Post by 3rdalbum on 2009-03-04
Every hard disk must be mounted into a folder on the filesystem; i.e. when you open the folder, the contents of your disk are there. This is called a "mount point".

When you plug in an external hard disk, Gnome and KDE usually mount it in a directory inside /media. They find the disk label and use that as the name of the mount point.

You can have your /home or /usr or whatever on a seperate hard disk, just by having Linux mount another hard disk into the /home mountpoint, or /usr mountpoint.

A second internal hard disk won't mount itself - you need to specify a location in /etc/fstab. This doesn't have to be in /media - for instance, my third HDD is mounted at /Terrabyte.

---

### Post by Firestem4 on 2009-03-04
Ok cool. Thank you for the information!

---

