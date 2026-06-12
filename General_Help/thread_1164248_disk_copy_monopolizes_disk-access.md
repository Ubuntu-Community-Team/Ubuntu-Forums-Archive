---
title: "disk copy monopolizes disk-access?"
date: 2009-05-19
forum: General Help
---

### Post by bsmith1051 on 2009-05-19
Is there a way to de-prioritize disk-to-disk copies so that you can still use the disk for other apps?  This has been a problem for years and I keep thinking that newer versions of the "Completely Fair" scheduler will fix the problem, but now I think I have to customize something.

Here's an example:
- I have fast system (X2 5200) and with plenty of memory (3 GB)
- my main data-drive is a RAID-1 sw array (SATA) and my secondary is a generic PATA; both are formatted with EXT3
- whenever I'm copying files between drives, I can't get anything else to open until the copy is complete.  If I already have a program open, however, it'll generally continue to work ok (e.g. Firefox).

---

### Post by zoubidoo on 2009-07-24
I agree.  This problem has been going on for years now.  I ranted about it earlier today.
[http://ubuntuforums.org/showthread.php?t=1221881](http://ubuntuforums.org/showthread.php?t=1221881)

---

