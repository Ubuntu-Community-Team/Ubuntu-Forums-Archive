---
title: "DMA Mode?"
date: 2005-10-25
forum: Desktop Environments
---

### Post by wrynn on 2005-10-25
How can i tell if my hard drive is in DMA mode? i ran the DMA section on Automatix, but i think thats just for cdrom drives right?

---

### Post by jasmuz on 2005-10-25
sudo hdaparm /dev/hXX

Substitute X with your info

and no, its for any kind of disk drive.

---

### Post by wrynn on 2005-10-25
command not found

---

### Post by jadugarr on 2005-10-25
He made a typo, it should be
sudo hdparm /dev/hXX

---

### Post by nix4me on 2005-10-25
Its hdparm.

---

