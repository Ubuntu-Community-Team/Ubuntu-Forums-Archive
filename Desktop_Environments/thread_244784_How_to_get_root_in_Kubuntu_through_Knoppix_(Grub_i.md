---
title: "How to get root in Kubuntu through Knoppix (Grub is broken)"
date: 2006-08-26
forum: Desktop Environments
---

### Post by voltronguy on 2006-08-26
OK, I moved my Linux partitions around and when I boot Grub immediately gets an error.  I'm hoping that changing menu.lst to point to the new partition will take care of it.

The problem is that I am in Knoppix right now.  I can't figure out how to get root in my Kubuntu installation so I can get write access on the menu.lst file.

Any other suggestions?

---

### Post by voltronguy on 2006-08-26
OK, I used ultimate boot disc to repair Grub to the point that I can at least boot into Windows again.  So at least I have my computer back in some form.  My question still stand though, what would be the best way to be able to edit grub to point to the new partition?

Thanks for any help.

---

### Post by aysiu on 2006-08-26
I believe there's a *Konqueror Superuser Mode* launcher in the KMenu somewhere in Knoppix. If you can't find it, just open a terminal and type ```
su
konqueror
```

---

