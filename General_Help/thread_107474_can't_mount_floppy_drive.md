---
title: "can't mount floppy drive"
date: 2005-12-23
forum: General Help
---

### Post by Danielle on 2005-12-23
hi, i'm not desparate to fix this, but it would be good. Ubuntu can't mount my floppy drive. it's not the best drive because i sometimes have to move the disk around abit for it to sit correctly. however, i think i have tried enough times for it to have worked if it was going to.

it is setup correctly, have are the settings from sudo gedit /etc/fstab
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

is there anything else i can try? thanks

this is the error message i get:
Warning: device /dev/fd0 is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount

---

### Post by Danielle on 2005-12-23
i fixed it with this:
sudo  mount -t vfat /dev/fd0 /media/floppy0

i think i'm starting to get the hang of this Linux stuff :razz: i know i'll regret saying that, oh well.

---

