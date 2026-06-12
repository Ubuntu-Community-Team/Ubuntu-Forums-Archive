---
title: "Grub menu messed up by latest linux image upgrade"
date: 2008-05-27
forum: Desktop Environments
---

### Post by Terrycymru on 2008-05-27
Update-grub did not adjust the value of the default booted system when I upgraded today although my options are set to do so.

In this line in boot/grub/menu.lst the default was changed from 0 to 2 (i.e. the value for the old linux image): 
```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

```

The solution is to edit menu.lst back to default  0 (assuming you wish to boot to the latest linux image by default.)

---

### Post by meierfra. on 2008-05-27
I'm trying to understand why this happened. Do you have

# updatedefaultentry=false

or 

# updatedefaultentry=true

in menu.lst?

---

### Post by Terrycymru on 2008-05-28
> **meierfra. said:**
> I'm trying to understand why this happened. Do you have

# updatedefaultentry=false

or 

# updatedefaultentry=true

in menu.lst?

I have # updatedefaultentry=true but grub update seemed to ignore it. No one else has confirmed a similar experience.

I have subsequently removed an old linux image and the default entry was updated as expected. Weird.

---

### Post by meierfra. on 2008-05-28
```
# updatedefaultentry=true
``` 

This is your problem. It tells grub to make sure  that whatever  title currently  is  the default stays the default during updates.

Change it to "# updatedefaultentry=false" and your problem is gone.

---

### Post by Terrycymru on 2008-05-28
Thanks, meierfra. :)

---

