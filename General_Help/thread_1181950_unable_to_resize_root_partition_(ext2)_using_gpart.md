---
title: "unable to resize root partition (ext2) using gparted &gt;&gt;&gt;"
date: 2009-06-08
forum: General Help
---

### Post by wamanning on 2009-06-08
i'm trying to expand my root partition to take up the unallocated space on my drive.  the ubuntu root is in a secondary partition if it matters (/dev/sda5).  the drive is clean with no errors reports from vista (for the root partition -- it's been defragged/chkdsk'd many times) and gparted reports no problem with /dev/sda5.

i'm running gparted from a live-cd so /dev/sda5 is not mounted.

here are some screen shots - any ideas?

[img]http://brown-snout.com/misc/2009_trouble_with_linux/IMG_0057.JPG[/img]
[img]http://brown-snout.com/misc/2009_trouble_with_linux/IMG_0058.JPG[/img]
[img]http://brown-snout.com/misc/2009_trouble_with_linux/IMG_0059.JPG[/img]

---

### Post by michy99 on 2009-06-08
The logical partition sda5 is inside the extended partition sda2. You must expand sda2 first.

---

### Post by wamanning on 2009-06-08
duh!  that did it...thx a ton!

---

### Post by bootdoc on 2009-06-19
I want to do the same thing.  Did you make backup and do you feel it is necessary?
did you lose any data in the process?

---

