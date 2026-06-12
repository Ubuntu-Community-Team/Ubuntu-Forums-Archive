---
title: "Possible NTFS issue?"
date: 2005-11-10
forum: Desktop Environments
---

### Post by devinjd on 2005-11-10
After upgrading to Breezy I am having issues when I access any of my NTFS drives/partitions (I have an external NTFS and my Windows partition is NTFS).  Anyway, when I try to load my music into Amarok or Rhythmbox, the directory scan starts off fine, but then slows to a crawl.  I even have trouble moving my mouse.  It kind of skips around...as if my entire system is pausing every second or so.  The same thing happens when I try to browse directories in Nautilus.
Also, my CPU usuage jumps to 100% and my CPU is scaled all the way up to max.
Any ideas what the issue is?  I thought Breezy was supposed to have improved NTFS access.  

Thanks in advance
~Dev

---

### Post by DrBair on 2005-11-10
Is this a problem when accessing off your internal or external drive?  If its internal, is it a SATA drive? Also if internal, is it a separate drive from the one that ubuntu is loading off of?

Also, are you using captive-ntfs or the native linux driver? If you're not sure then its probably the native linux driver.

---

### Post by Juzz on 2005-11-10
Which driver is more feature rich?

I have an NTFS partition that I would like access to, but the linux native can't mount it (a 120GB SATA disk where the partition fills the entire drive)

---

### Post by manicka on 2005-11-10
The other problem that you'll have is that ntfs partitions are read only, so you won't be able to do any tag editing etc.

Try to use fat32 if possible.

---

### Post by RAOF on 2005-11-11
[QUOTE=Juzz]Which driver is more feature rich?

I have an NTFS partition that I would like access to, but the linux native can't mount it (a 120GB SATA disk where the partition fills the entire drive)[/QUOTE]
If you have a copy of Win2K or XP, [Captive-ntfs]("http://www.jankratochvil.net/project/captive/") loads the actual windows NTFS driver, and so allows full read-write access to an NTFS drive.  Odd, though.  I've mounted a 120+GB NTFS partition from a SATA drive using the native linux driver before.

---

