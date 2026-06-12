---
title: "iso max 350MB on remote win share?"
date: 2006-01-14
forum: General Help
---

### Post by matva on 2006-01-14
i'm trying to copy a DVD ISO from my win machine to my ubuntu machine. For whatever reason, ubuntu only sees the 4.7gb image as ~350MB. Same goes for any dvd iso image file. Any suggestions?

Also, i still have some windows partitions on this comp that show on the Desktop. How do i make them accessible from the Desktop (says i dont have permission)?

---

### Post by curuxz on 2006-01-14
Windows partitions start off under the control of root only, hence why you cant access them. The quickest way to change them is from KDE control center but being a gnome user you will probs have to do it the old way, look on the forums  fstab, thats the file which controls it there are loads of posts on how to change it for that.

as for the images, have you verified they are whole. You should be able to get an hash or checksum for a downloaded iso that you can compare to make sure its not damaged. That would be my first stop off :)

---

### Post by matva on 2006-01-14
yep, they're definitely whole.

---

