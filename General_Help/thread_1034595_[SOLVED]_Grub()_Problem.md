---
title: "[SOLVED] Grub(?) Problem"
date: 2009-01-08
forum: General Help
---

### Post by chiefbutz on 2009-01-08
Ok, so for reasons I don't want to explain I had to install Wubi and then move the image to a partition to reinstall Ubuntu. When I moved the image over as specified the /boot/grub/menu.lst was not correct when I tried to boot. For an entry it looked like this:

```

title Ubuntu 8.10, kernel 2.6.27-7-generic
root ()/ubuntu/disks
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=8c585a4d-278e-4564-a670-f16c778d75b7 ro ROOTFLAGS=syncio quiet splash 

```

I managed to change the root line to that it looked like this:
```
root (hd0,6)
```

I just updated and when it updated it wanted to change the root line for the new entries to the messed up format. Is there any way to keep it from trying to do that?

---

### Post by thedarkwinter on 2009-01-09
Hi

If you are changing partitions etc, its best to reconfigure grub and let it autodetect. Reasons being the partition numbers and UUID's will be different. If you can boot into ubuntu, run ```
sudo update-grub
```, otherwise you may need to boot from the live cd an install from there.

cheers,
michael

---

### Post by chiefbutz on 2009-01-09
Thank you

---

