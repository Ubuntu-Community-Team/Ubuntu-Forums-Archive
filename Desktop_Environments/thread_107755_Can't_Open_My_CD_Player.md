---
title: "Can't Open My CD Player???"
date: 2005-12-23
forum: Desktop Environments
---

### Post by Hangetsu on 2005-12-23
Hello all!

This is probably something newbish, but I have a new Breezy Badger install, all looks well (now that the wireless issues are resolved) EXCEPT I cant open my CD ROM drive or DVD ROM drive.  I press the buttons and nothing happens.

The drives are recognized (I can see and access the contents from File Browser), but that's about it.

Any ideas on what to check first?

Thanks!

---

### Post by DaMasta on 2005-12-23
Mine does that too. 
sudo eject /cdrom
Then you should be able to manually open the tray.

---

### Post by darth_vector on 2005-12-23
is there anything inside the cd player? if so it is probably mounted. a

umount /media/cdromx

will unmount it (where x is the number of the cdrom device) and then you should be able to open and close the thing at your leisure.

---

### Post by Hangetsu on 2005-12-23
*blush*  Yes, there are disks in the drives, so they were mounted.  

I work with AIX machines, I should have known that.  Thanks much!

---

