---
title: "Unable to boot Ubuntu after partition table problems"
date: 2006-06-24
forum: Desktop Environments
---

### Post by Chribu on 2006-06-24
I had a few problems with the partition table, after deleting an EXT2 partition from windows while it was still mounted with EXT2FS (silly me ](*,) )
I've managed to get windows XP working again with XP install disc and then managed to reinstall grub with Ubuntu install cd, but now this is what I get when trying to boot ubuntu.

[IMG]http://www.chribu.com/tmp/ubuntu1/1.jpg[/IMG]

Hope i can get some help here :)

---

### Post by Chribu on 2006-06-24
Ok, booted with ubuntu setup-live cd, mounted linux partition, there i edited /boot/grub/menu.lst so that it would point to the right partition.
Then grub, root(hd0,2), setup(hd0)

---

