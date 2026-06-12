---
title: "Grub error 17"
date: 2009-01-11
forum: General Help
---

### Post by agm_ultimatex on 2009-01-11
I was running a dual boot of xp and ubuntu on my dell laptop (came with xp, not ubuntu). I decided to use gparted to format the small ubuntu partition, as I wanted to try out windows 7 beta. After formatting it, and creating a new partition with gparted, grub loader is still appearing on boot, and gives me an error. Any ideas on how i can fix this? I do have most important stuff backed up on my memory stick, aside from a word doc i worked on yesterday for school.

---

### Post by chex_m8 on 2009-01-11
when you formatted the ubuntu partition you wiped out all the boot files neede for grub. if i understand you correctly you now have xp and windows 7 only on this HD.

---

### Post by caljohnsmith on 2009-01-11
It sounds like you just need to restore a Windows MBR (Master Boot Record) to your drive. If you have a Windows Install CD, you can do the following from the "recovery console" on the CD:
```
fixmbr
```
And that will reinstall a Windows MBR. If you don't have a Windows MBR, you could boot your Ubuntu Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
And that should accomplish the same thing. Let me know how it goes or if you run into problems.

---

### Post by chex_m8 on 2009-01-11
yeah, that should do it thanks caljohn

---

### Post by agm_ultimatex on 2009-01-11
> **caljohnsmith said:**
> It sounds like you just need to restore a Windows MBR (Master Boot Record) to your drive. If you have a Windows Install CD, you can do the following from the "recovery console" on the CD:
```
fixmbr
```
And that will reinstall a Windows MBR. If you don't have a Windows MBR, you could boot your Ubuntu Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
And that should accomplish the same thing. Let me know how it goes or if you run into problems.

grabbed my sp1 out of my closet, did the fixmbr. Seems to be good so far. Thank you :)

---

