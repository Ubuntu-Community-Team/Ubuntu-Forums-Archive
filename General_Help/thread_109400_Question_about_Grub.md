---
title: "Question about Grub"
date: 2005-12-28
forum: General Help
---

### Post by hexedecimal99 on 2005-12-28
Is their anyway I can set grub to boot to Windows by default, but still have Ubuntu on the list?

---

### Post by psusi on 2005-12-28
Yes, edit your /boot/grub/menu.lst.  The comments should explain what to change.  

You can also change the line:

default 0

to:

default saved

And grub will remember your last choice and default to that.

---

### Post by Iandefor on 2005-12-28
open up /boot/grub/menu.lst for editing as root. If you don't know how to do that, open up a terminal and type in ```
sudo 'evim /boot/grub/menu.lst'
``` the first lines should look something like this:  ```
#menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default        0
``` change the default option to whatever number the Windows boot option is; for instance, if it's listed as the second option, set default to 1 (remember, it starts counting from 0), save and quit. I encourage you to read the man pages it lists in menu.lst if you plan to do much more playing around with grub.

---

### Post by Kawayanan on 2005-12-30
I have a quick follow up to this.

I have a dual bot with WinXP which I made default (for the wife and child - they aren't converted yet :p ).  When I did an update that included a new kernel though, things get changed.  The update added grub entries for the new kernel (and recovery mode for it).  These were added to the top of the grub list, so what was default to WinXP (default 4) became a default to the memory test.  This was easy enough to fix, but is there a way to keep this from happening?  I moved the WinXP to be the first on the list (and set "default 0").  I think that the next time I update a kernel though, the new kernel entry will be put on top of the grub list again.   Any thoughts on this?

Kawayanan

---

### Post by juantxorena on 2005-12-30
Kawayanan -> You must erase the entries for the old kernel every time you install a new kernel, because you won't use them again. Then the windows entrie must be on the same place.

Also, you must remove old kernel packages using synpatic, or the like (it's not necessary, but it's quite logical). I don't know if the old entries in grub list are erased when removing the old kernel packages, I've never tried. I always have a look to the grub list when installing a new kernel, just in case.

---

