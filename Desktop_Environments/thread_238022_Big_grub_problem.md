---
title: "Big grub problem"
date: 2006-08-17
forum: Desktop Environments
---

### Post by elizleisndahizle on 2006-08-17
So I turned my computer off and it locked up so I held the power button and turned it off.  When I turned it back on it got past the bios stuff and now it just says GRUB in the top lefthand corner of the screen and does absolutely nothing after that.

---

### Post by philippe_carlo on 2006-08-17
Ouch, that does not sound very encouraging. Try booting with a live CD and see if you can mount your hard disk there. If you can, then you should probably check the disk with fsck. If that check passes, you may want to try grub-install (see the docs) to restore grub in the MBR.

---

