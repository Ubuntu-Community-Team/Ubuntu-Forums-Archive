---
title: "File Permission on external drive"
date: 2008-12-04
forum: General Help
---

### Post by bobbert68 on 2008-12-04
I am unable to delete the files on my external HDD (NTFS).  I tried changing the permissions with chown and chmod, but nothing happened.  I also tried opening Thunar as root and changing the permissions that way.  I was still unable to make changes on most of the files and was given the error: "Read-only file system".  How can I get full control over my files?

Thanks

---

### Post by vanadium on 2008-12-04
An external ntfs drive normally is fully readable/writable by default under recent versions of Ubuntu.

Before trying to do anything else, check the disk under Windows. Connect the disk on a Windows system, have the disk checked using the Windows disk checking tools and then *completely* shut down Windows (no hibernate or standby!). Alternatively, you can use the "Safely remove hardware" icon to disconnect the drive.

At that point, your file system will be "clean". Next time you connect it to an Ubuntu system, you will be able to read and write.

---

