---
title: "grub reinstall error :("
date: 2006-01-01
forum: Desktop Environments
---

### Post by Iuliux on 2006-01-01
> ubuntu@ubuntu:~$ sudo grub-install /dev/hda
Probing devices to guess BIOS drives. This may take a long time.
/dev/mapper/casper-snapshot does not have any corresponding BIOS drive.
ubuntu@ubuntu:~$
is this bad? i really want to reinstall grub. i have lost it when i've deleted one partition.

---

### Post by makro on 2006-01-01
Try to add --recheck option

---

### Post by Iuliux on 2006-01-01
still the same thing :( > ubuntu@ubuntu:~$ sudo grub-install /dev/hda --recheck
Probing devices to guess BIOS drives. This may take a long time.
/dev/mapper/casper-snapshot does not have any corresponding BIOS drive.
ubuntu@ubuntu:~$


---

### Post by Iuliux on 2006-01-01
my kubuntu is installed on hda7 and the bootloader i was using was installed on mbr.

---

