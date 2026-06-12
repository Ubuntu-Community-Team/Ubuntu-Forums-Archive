---
title: "no entries highlighted in grub menu"
date: 2006-06-26
forum: Desktop Environments
---

### Post by dspivey on 2006-06-26
when i start my system and the grub menu comes up, none of the entries are highlighted.  even when i use the up and down arrow keys, there is no highlighted area to let me know which entry I have selected.  I tried reinstalling grub to no avail.  I'm sure there's an easy resolution to this, but I haven't been able to find one in the forums to this point.  Any help is greatly appreciated!

---

### Post by caserio on 2006-06-26
Hi,

This may happens if you change the default bootsplash theme...

---

### Post by dspivey on 2006-06-26
thank you, caserio.  I tried reinstalling usplash but this didn't help.  what steps should i take to reset to the default bootsplash?

---

### Post by dspivey on 2006-07-03
bump

---

### Post by dspivey on 2006-07-08
bump...


anyone?  please????

---

### Post by phansiizwe on 2006-07-09
Hi dspivey,

maybee there's an incorrect 'default' selection in /boot/menu.lst.

The section looks like:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0
```

If this isn't set to zero, that might be the problem.

!Do not edit anything else in this file, it might stop your computer from booting properly!

---

### Post by dspivey on 2006-07-10
thank you very much for your reply, phansiizwe!

I checked the menu.lst file and the default was set to 0.  
it seems to be a problem with grub gui itself.  i'm open for any and all other suggestions anyone may have.

---

