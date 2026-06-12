---
title: "[SOLVED] XP &amp;amp; Wubi: &amp;quot;No OS detected&amp;quot;"
date: 2009-01-04
forum: General Help
---

### Post by shoeheight on 2009-01-04
Hello,

I just reinstalled XP (sp3), downloaded the Ibex torrent (8.10-desktop-i386) and attempted to install it with Wubi.  The plan was to copy it to a local file and run the Wubi magic, but I instead ran it from the CD (oops...I guess) and attempted to install it to my C: drive.  The install appeared to go great but after complete installation I found my computer booting to "No OS detected".  

I can boot my system by forcing it to boot a 8.10-desktop-i386.iso CD then getting the Ubuntu disk to "boot from harddrive" (an option on the ubuntu startup splash screen) and choosing "windows XP" or "Ubuntu"

I attempted to fix it by running my XP (as described above) and deleting Ubuntu from XP with the "ad/remove programs".  This worked, but I still get the "No OS detected" at startup.

I'd rather not reinstall XP AGAIN and have to download all those patches....again.....

any suggestions?  

FYI The system is an Inspiron 5100

THANKS SO MUCH!

---

### Post by shoeheight on 2009-01-05
Sorry, this issue is now fixed.

This was not a Wubi problem, it had to do with the boot order of my BIOS....easily fixable.

---

