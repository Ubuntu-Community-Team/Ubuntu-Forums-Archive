---
title: "GRUB keeps reverting to old UUID setting - HELP!"
date: 2009-06-15
forum: General Help
---

### Post by mojo on 2009-06-15
Hi everyone
   I installed Ubuntu Jaunty on my system with following fs settings:

/boot - 200MB
/ - 49GB

After playing around, I got /boot corrupted... (sound really bad rite?) So what I did is to rescue it by remove completely /boot parittion; create folder '/boot' on my '/' partition then copy all files within '/boot' folder (which I backed up before messing things up) to the new '/boot'. And ofcourse I have to modify the menu.lst to make sure the UUID match the '/' partition.

All works nicely until IF I upgrade to newer kernel image, the GRUB reverts menu.lst UUID to the old-deleted '/boot' partition. Can someone help me to enforce it to use the '/' UUID?

---

### Post by oldos2er on 2009-06-15
Did you edit your /etc/fstab file to reflect the partition changes?

---

### Post by unutbu on 2009-06-15
In /boot/grub/menu.lst check for lines that looks like this:
```

## default grub root device
## e.g. groot=(hd0,0)
# groot=**1f57f1e1-a3a8-4b83-998f-36bfeed2d3c9**
```

Make sure the UUID is correctly set here.

Despite beginning with a # symbol, this is not a comment. The update-grub script reads lines that begin with a single # and uses options written on these lines to rewrite your menu.lst.

When you upgrade your kernel, update-grub is run.

---

### Post by mojo on 2009-06-15
@unutbu: a clear, precise and straigh-to-the-point answer, the issue is resolved. thanks much

---

