---
title: "fedora files access using ubuntu"
date: 2009-02-28
forum: General Help
---

### Post by kask1984 on 2009-02-28
hi every body. one of my friend installed fedora 9, windows xp and ubuntu 8.10. when systems starts booting fedora 9 is not displaying.
please tell me how to enter into fedora 9 and how to access fedora files from ubuntu (as we can access xp files).
thanks in advance

---

### Post by taurus on 2009-02-28
First, you need to mount the partition where F9 is, assuming it's /dev/sda2 to /media/fedora.

Then, you need to look at the entry in /media/fedora/boot/grub/grub.lst for F9 and copy those lines to your /boot/grub/menu.lst (in Ubuntu).

---

