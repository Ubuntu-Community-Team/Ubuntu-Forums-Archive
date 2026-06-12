---
title: "grub"
date: 2005-11-07
forum: Desktop Environments
---

### Post by thrust on 2005-11-07
when i startup my comp grub has ubuntu selected by default and then boots. i was wondering if there was a way to change the default selection to another OS
thx
matthew

---

### Post by Xian on 2005-11-07
Just edit your /boot/grub/menu.lst file and change the 'default' entry in the section below to reflect the sequence number of the OS you would like to boot by default.

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		2
```

---

### Post by aysiu on 2005-11-07
Count how many entries you have. Then, minus one. That's the number default should be. For example, if you want the third choice to be default, then default should be 2. If you want the fifth choice to be default, then default should be 4.

To edit your Grub, type this in a terminal (Konsole): ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
kdesu kwrite /boot/grub/menu.lst
```

---

### Post by Xian on 2005-11-08
Or you could just move the desired OS entry to the top. :)
My rule: avoid even simple math. ;)

---

### Post by Navyblue on 2005-11-08
My rule is to change a number rather than to move a chunk of text. :p

---

### Post by thrust on 2005-11-08
thanks fer the help guys i know what do to now
matthew

---

