---
title: "/windows with dual-boot install"
date: 2007-08-26
forum: Development CD/DVD Image Testing
---

### Post by miked34 on 2007-08-26
I was installing Tribe 5 of 7.10 (amd64) today on a dual-drive SATA machine with Windows XP dual-boot.  I was using "manual" partitioning since I did not want the installer to overwrite my Windows partition.

The installer froze every time without any indication that something was wrong (progress bar showed x% but it was not doing anything for a LONG period of time).  After some trial and error, I traced the problem to the fact that I was selecting "/windows" for where to mount my WinXP partition.  This seems to cause problems in the current installer.  When I left the default value alone ("/media/sda3"), the install continued without problems.

Could be something else, but it seems like the installer may not like it when you tell it to mount an existing partition in the target's root.

-Mike

---

### Post by w4ett on 2007-08-27
Mike--you might want to report a bug on that problem.

[http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

