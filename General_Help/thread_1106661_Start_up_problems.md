---
title: "Start up problems"
date: 2009-03-25
forum: General Help
---

### Post by rusty spork on 2009-03-25
When my computer boots up I get this message when I try to run Ubuntu through the grub boot loader:

```
Boot from (hd0,4) ext3  cf69793f-2662-4795-a6c1-a203c521aa50

Error 1: Filename must be either an absolute pathname or blocklist

Press any key to continue...
```

Pressing a key takes me back to the boot loader menu.  I used to be able to boot Ubuntu by using one of the two recovery options, although, recently, the first recovery option won't work.  Now the only way I can boot, is by going through recovery, then resuming the boot into ubuntu.

---

### Post by evilaim on 2009-03-25
remove: "savedefault"
from the menu.lst

---

