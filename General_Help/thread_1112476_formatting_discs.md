---
title: "formatting discs"
date: 2009-03-31
forum: General Help
---

### Post by celticJedi on 2009-03-31
Hi, I know this is probably really obvious but I'm a little stuck. I have an old 2.5 hard disc in a caddie that I want to use as a back-up drive. It used to be in a laptop running an old version of linux (I forget which flavour) so it's full of all the old system files. I've tried deleting them but I get a permission denied error. How can I re-format or clean the drive?

---

### Post by adult swim on 2009-03-31
if youve got ubuntu now, run ```
sudo apt-get install gparted
``` then plug in the drive, make sure it is unmounted and go to System>administration>partition editor and you can format the drive from there

---

### Post by _Purple_ on 2009-03-31
Check [this](http://ubuntuforums.org/showthread.php?t=789037) out.

---

### Post by celticJedi on 2009-04-01
> **adult swim said:**
> if youve got ubuntu now, run ```
sudo apt-get install gparted
``` then plug in the drive, make sure it is unmounted and go to System>administration>partition editor and you can format the drive from there

that's great, but as I'm a complete newbie as far as file systems and partitions go, what's the recommended settings? (I've got about 18GB to play with)

---

