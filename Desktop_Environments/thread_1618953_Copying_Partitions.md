---
title: "Copying Partitions"
date: 2010-11-11
forum: Desktop Environments
---

### Post by Geffers on 2010-11-11
If I copy or clone an ubuntu system onto a different drive  what alterations do I have to do to make it bootable.

I've done this on numerous occasions using Norton on Windows but I understand the partition boot sector or MBR needs to be adjusted.

Geffers

---

### Post by sanderd17 on 2010-11-11
once you've installed your hard drive into an other machine, run a grub rescue disk (you can also do it with the ubuntu live CD) and reinstall grub (grub only). there are tutorials on the net, just search for "rescue grub".

---

### Post by Geffers on 2010-11-13
> **sanderd17 said:**
> once you've installed your hard drive into an other machine, run a grub rescue disk (you can also do it with the ubuntu live CD) and reinstall grub (grub only). there are tutorials on the net, just search for "rescue grub".

Thanks, the search for 'grub rescue' was useful.

I was quite familiar with grub-legacy but as yet I can't get my head round Grub2.

I've often wondered if grub-legacy and grub2 can both be installed side by side but that would probably cause problems.

Geffers

---

