---
title: "format drive in NTFS using command line"
date: 2009-05-27
forum: General Help
---

### Post by creamcheeze77 on 2009-05-27
I recently installed ubuntu server (9.04) on another computer, wanting to use it as a simple file server.  Everything went smoothly, except that i want to use the 450 GB partition on the main drive and the other 500gb drive for storage -- accessible by windows machines, so i have to partition them as NTFS.  normally i'd just use gparted, but i disconnected the CD drive in the server.  is there any way to format the drives using the command line?

---

### Post by creamcheeze77 on 2009-05-27
so, I finally manned up and hooked up the CD drive again and used gparted to format the partitions -- i reformatted sda1, as NTFS and made all of sdb NTFS.  deleting my operating system.  when i reinstall, do i create a new partition from sda1, and if so, how big?  i want to be able to use as much of the drive as possible for storage.  i'm trying to avoid having to install again.  thanks guys.

---

