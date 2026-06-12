---
title: "Difference between root an rootnoverify in grub menu"
date: 2009-06-03
forum: General Help
---

### Post by lindsay7 on 2009-06-03
What is the difference in meaning between root and rootnoverify in the grub menu?  When would you need to choose one over the other?

---

### Post by Entropy_Sam on 2009-06-03
According to the page at [http://orgs.man.ac.uk/documentation/grub/grub_13.html#SEC99](http://orgs.man.ac.uk/documentation/grub/grub_13.html#SEC99) rootnoverify is for filesystems which GRUB doesn't specifically recognise. With this command, it just "points" to the drive, rather than trying to mount it.

---

