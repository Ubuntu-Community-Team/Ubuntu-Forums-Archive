---
title: "constant superblock error on USB hardrive at boot"
date: 2006-07-11
forum: Desktop Environments
---

### Post by paridoth on 2006-07-11
nearly everytime i boot, during the filesystem check, i get an error that my usb hardrive (/dev/sdc1) has a corrupted superblock, so i repair it using 
```
e2fsck -b 32768 /dev/sdc1
```
first it tells me i dont have a large file support flag set, and i tell it to fix it, but everytime i boot it tells me the same thing, and i fix it again, then i get hundreds of block count and something else count errors, so many that i have to just hold down the y button for a good half a minuet if not more so that it fixes them all. 

i dont understand why this keeps comming up, whenever i remove my hardrive i unmount it first, or shutdown my computer fully before turning it off, why does this keep hapening?

---

