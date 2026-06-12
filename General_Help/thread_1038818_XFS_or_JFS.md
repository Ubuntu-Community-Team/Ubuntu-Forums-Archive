---
title: "XFS or JFS"
date: 2009-01-13
forum: General Help
---

### Post by Grant A. on 2009-01-13
Can Xubuntu boot from XFS or JFS?

---

### Post by perlluver on 2009-01-13
It should boot from both, but JFS is a safer bet, XFS says something to the effect that Grub will not load properly with it.

---

### Post by deanjm1963 on 2009-01-13
Both are very good, JFS uses grub bootloader, just like ext3 et al, xfs uses lilo.

Both are very quick at mounting drives, but I would go for JFS, just my personal preference, I have used both and prefer JFS.

---

### Post by Grant A. on 2009-01-13
Thank you both very much for your replies. I will go with JFS then. :D

I would thank you using the Thanks System, but unfortunately it has been disabled due to database issues. Sorry. :(

---

### Post by bodhi.zazen on 2009-01-14
You can use either JFS or XFS.

To use grub with XFS you need a separate /boot partition. You can make a small ext2 partition and use it for /boot . With this configuration you can then use grub and boot a XFS root ( / ) partition.

I think the question should be what are you wanting to accomplish by using JFS or XFS ?

---

