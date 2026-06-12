---
title: "Vista Dual Boot Error 17 - Just want to save files from Ubunu Drive!"
date: 2009-04-27
forum: General Help
---

### Post by ondi on 2009-04-27
I had a system with Ubuntu 9.04 only, which ran fine.

This morning I installed Vista on a separate hard drive, which worked fine.

However, now when I try to start Ubuntu i get error 17. I've tried using the Live CD and going through terminal and doing it that way, but I have no luck.

My main aim is to salvage my documents from my Ubuntu drive.

I've tried using Ext2 to load the Ubuntu drive in Windows, but Ext2 seems to do nothing... at all. My two hard drives appear in Ext2, but I can't do anything with them!

Can anyone help? Thanks

---

### Post by Sef on 2009-04-27
Vista overwrote GRUB.   Get [Super GRUB Disk]("http://www.supergrubdisk.org/") to reinstall GRUB easily.  GRUB sees both GNU/Linux and nonGNU/Linux operating systems; Microsoft's bootloader sees only Microsoft operating systems.

---

### Post by ondi on 2009-04-27
thanks for your reply. I tried using the SGD but get the following errors

```
 Booting 'trying /grub/stage1 /boot/grub/stage1'

selectfile /grub/stage1 /boot/grub/stage1


GRUB Error 15: file not found 
  Booting 'not lucky'

pause SGD has not succeeded :(
SGD has not succeeded :(
```

---

