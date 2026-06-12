---
title: "Copy boot data to other partition"
date: 2009-01-28
forum: General Help
---

### Post by djbushido on 2009-01-28
Okay, I am wanting to copy my MBR and boot sector data to another partition, because [dd isn't working]("http://ubuntuforums.org/showthread.php?t=1052080") and I was just going to copy files over. I am wanting as posted to copy both the MBR of the disk and each partitions boot data, as I am dual-booting. Also, does GRUB need a specific install, or does it just look for grub.conf?

---

### Post by cmnorton on 2009-01-30
As I remember there are rules as to where the MBR can go. You might want to look at the grub documentation.

---

### Post by djbushido on 2009-02-03
Okay, I just installed GRUB again. This fixed it.

---

