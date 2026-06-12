---
title: "Editing the boot record"
date: 2005-12-15
forum: General Help
---

### Post by SomethingTohide on 2005-12-15
Is there anyway I can edit the MBR so I can make Windows XP the first in the list, because I'm tired of wanting to run XP but going to the bathroom and coming back to see it in Ubuntu, and when the power goes out and I'm sleeping, instead of booting into windows and reopening the apps, it goes into Ubuntu.

---

### Post by schilcha on 2005-12-15
Edit the file /boot/grub/menu.lst (sudo gedit /boot/grub/menu.lst)

There you'll find a section like this...
```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default         0

```

Change the number in the last line (following "default") to the position of your xp-entry in the boot-selection-list. MIND that numbering starts at zero! (Anyhow, the comments in the file are highly helpful)

After you're finished, just reboot and see...

---

### Post by mherring on 2005-12-15
Just add a semantic nitpick:  Following the instructions above, you are not "editing the MBR".  (Nor do you WANT to edit the MBR!!!)

---

