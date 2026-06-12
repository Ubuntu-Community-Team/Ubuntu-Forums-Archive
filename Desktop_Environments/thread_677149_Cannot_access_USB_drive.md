---
title: "Cannot access USB drive"
date: 2008-01-24
forum: Desktop Environments
---

### Post by nprignano on 2008-01-24
I have Ubuntu 7.10 desktop (GNOME) installed, and I can no longer access my USB drive, which I was able to access with a clean install.  I have not made a backup recently, and would like to resolve the issue without restoring a backup if at all possible.  I am an Ubuntu newbie, so any help would be greatly appreciated.

---

### Post by taurus on 2008-01-24
When you said you can no longer access the USB drive, do you mean it didn't automount or you couldn't write or read from it?  What format is that USB drive?

Open a terminal and post the output of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
mount
```

---

