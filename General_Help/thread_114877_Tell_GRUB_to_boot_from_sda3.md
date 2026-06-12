---
title: "Tell GRUB to boot from sda3?"
date: 2006-01-09
forum: General Help
---

### Post by ubuntuuser on 2006-01-09
Hi all. When creating a config file for GRUB, how do I tell him that he should use sda3 as root partition? I have sda1 as /boot and no other OS on that disk.

Thanks in advance.

---

### Post by kdevos on 2006-01-09
change the /boot/grub/menu.lst file and point the root to sda3

---

### Post by ubuntuuser on 2006-01-09
That would work with LILO, but GRUB needs something like hd(0,0). I need to replace hd with something (maybe sd?) and I need to replace the two digits with something else.

---

