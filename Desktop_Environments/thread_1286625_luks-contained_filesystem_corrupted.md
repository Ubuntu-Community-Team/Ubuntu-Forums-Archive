---
title: "luks-contained filesystem corrupted"
date: 2009-10-09
forum: Desktop Environments
---

### Post by agharbeia on 2009-10-09
Hello,
I a have an SD card which I use with an Eee 701. I create a LUKS container on the SD and host an ext3 in it.

The card itself is functional. I use normally in other scenarios.

The problem is that unless I manually umount the ext3 before I shutdown, the ext3 gets corrupted and is not possible to mount again.

When I mount manually, I notice that it takes slightly longer than what is expected in unmounting a clean, flushed file system. I understand SD may be slower than other storage devices. But is there a remedy?

The problem, in my specific situation, is complicated because I use a script to automatically mount the SD as my home upon booting, so I expect the whole operation to be seamless, or so I wish.

---

