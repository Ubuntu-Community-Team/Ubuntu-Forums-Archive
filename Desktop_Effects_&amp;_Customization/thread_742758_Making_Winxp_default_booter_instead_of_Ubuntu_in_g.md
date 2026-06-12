---
title: "Making Winxp default booter instead of Ubuntu in grub"
date: 2008-04-02
forum: Desktop Effects &amp; Customization
---

### Post by Lantesh on 2008-04-02
the grub menu is contained in boot/grub/menu.lst

Type this in terminal - ```
$ gedit /boot/grub/menu.lst
```

Look for this section near the top of the file, and make your change.  Notice my default is set to 4, not 0 which is the actual default setting.  I changed 0 to 4 to make my desired OS the new default.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		4

---

