---
title: "Annoying Reboot issue"
date: 2006-04-29
forum: Desktop Environments
---

### Post by chapium on 2006-04-29
I get the following error every single time i reboot and choose ubuntu from Grub:

```

Uncompressing Linux...
     crc error
--system halted

```

This doesnt happen if I cold boot.  How can I fix this?] (*,)

---

### Post by sYs^ on 2006-04-30
Is the selected kernel from repositories or did you compile it yourself?

---

### Post by Ramses de Norre on 2006-04-30
I found this: > I take it you are booting from a floppy? If so, write the kernel to another
floppy - the cyclic redundancy check error most likely indicates a physical
problem with the diskette.

If this is happening with a kernel booting from the HD, then it may mean
the same thing (physically damaged HD block), in which case you could try
booting from floppy, renaming the kernel image (so the bad block, if any,
can't get re-used), rebuild the kernel again (leaving the bad kernel alone),
and reboot.

If the problem really is a bad block, that might allow you to get the system
booted; then you'd have to fix up the bad block. Presumably e2fsck will do this,
if properly invoked?

---

### Post by chapium on 2006-05-01
I probably need to describe what is going on more.  This is with the latesst Ubuntu 5.10 kernel.  

This only happens if I reboot.  If I turn the computer off and back on, it works fine.

---

