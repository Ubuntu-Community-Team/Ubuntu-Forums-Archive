---
title: "Does gnome have a simple way to verify burned discs?"
date: 2005-12-16
forum: Desktop Environments
---

### Post by BoyOfDestiny on 2005-12-16
Hi, well I burned an ubuntu dapper iso (on an rw so no worries). I did check the iso file using cfv. However, how can I verify the disc burned without errors?

 dd if=/dev/cdrom bs=2048 count=310966 conv=notrunc,noerror | md5sum

I tried this command and it resulted in i/o errors.

Is there a simple or recommended known way to make it verify?

NOTE: I am using the nautilus built in cd/dvd burner (only thing that works on my breezy 64 box)

Thanks!

---

