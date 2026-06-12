---
title: "Reloading GRUB from live cd enviorment"
date: 2006-06-16
forum: Desktop Environments
---

### Post by spyke01 on 2006-06-16
i had a dual boot with ubuntu and xp on my drive, but xp took a nose dive and i had to reinstall. This of course killed grub and now i only have access to my nix info via the live cd, is there anyway i can reload grub from the live cd, i believe my menu.lst file is still intact, i just need grub put back on the mbr, any ideas?

---

### Post by bruce89 on 2006-06-16
I think ```
sudo grub-install /dev/hda1
``` would do it.

---

### Post by medya on 2006-06-16
i have the same question

---

### Post by bruce89 on 2006-06-16
[QUOTE=medya]i have the same question[/QUOTE]
I think ```
sudo grub-install /dev/hda1
``` would do it.

---

### Post by spyke01 on 2006-06-16
thanks man ill give it a try

---

### Post by spyke01 on 2006-06-16
ok this is what works to fix the problem
> 
sudo mkdir /mnt/hda3
sudo mount /dev/hda3 /mnt/hda3
sudo grub-install --no-floppy --root-directory=/mnt/hda3 --recheck /dev/hda

---

