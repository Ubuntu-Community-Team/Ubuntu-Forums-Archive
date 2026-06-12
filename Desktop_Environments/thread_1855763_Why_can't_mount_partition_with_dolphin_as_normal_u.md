---
title: "Why can't mount partition with dolphin as normal user?"
date: 2011-10-06
forum: Desktop Environments
---

### Post by bokopperud on 2011-10-06
I have computers with both Ubuntu and Kubuntu.  In Ubuntu I can mount a NTFS-partition as a normal user by simply clicking the drive in 'nautilus'.  In Kubuntu however, when I do the same and click on the drive in 'dolphin', I get an error for lacking privileges:
[INDENT]An error occurred while accessing (...), the system responded:
org.freedesktop.UDisks.Error.PermissionDenied: Not Authorized
[/INDENT] Is there a way to make Kubuntu/dolphin to work the same way for a normal user as in Ubuntu/nautilus?  How?

If I start 'nautilus' as root, I can mount them without problem, but I can't access them as a normal user afterward...  Is there a way to let a normal user access them afterwards?

---

### Post by oobuntoo on 2011-10-07
You can manually edit /etc/fstab to add NTFS partitions or you can install ntfs-3g and ntfs-config packages, THEN run NTFS Configuring Tool to add the partitions. You can do this from command line by typing:

/usr/sbin/ntfs-config-root

and just follow instructions.

---

