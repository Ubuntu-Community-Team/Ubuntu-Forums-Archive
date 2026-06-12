---
title: "Re-add windows to GRUB"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Ryutatsu on 2006-06-08
After I updated to Dapper it redid my GRUB menu which Breezy added windows to during installation now my windows is gone and I can't figure out exactly what to add back in. Is there a utility available that does the same thing as the installation or can someone suggest a way to determine exactly what to add to menu.lst? I've added a windows entry to the menu but I can't seem to figure out which partition I need to have GRUB point to.

---

### Post by scxtt on 2006-06-08
there should be a decent enough example of a windows grub entry in your /boot/grub/menu.lst file ... something like:

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

where (hd0,0) refers to the 1st partition on the 1st drive ... hd0 is the drive, and the 2nd 0 is the partition ...

---

