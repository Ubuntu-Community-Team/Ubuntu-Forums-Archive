---
title: "Grub"
date: 2005-07-16
forum: Desktop Environments
---

### Post by jcayo11 on 2005-07-16
How do I modify GRUB to let XP be the default OS on boot up.
Have dual boot XP and ubuntu
 ](*,)

---

### Post by art on 2005-07-16
In the /boot/grub/menu.lst edit the line saying default num, for example

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0


 change 0 to whatever you want.

---

