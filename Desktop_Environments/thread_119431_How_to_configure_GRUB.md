---
title: "How to configure GRUB?"
date: 2006-01-19
forum: Desktop Environments
---

### Post by kenquad on 2006-01-19
Hi all:

I've got a dual HD Kubuntu Breezy box with the other HD running MS Lose-dows 2000.  (Unfortunately my company runs some software that requires this dubious operating system.)  Anyway, I'd like to configure GRUB to load the other OS rather than having to change the boot sequence every time (which is exactly what I'm doing right now).  I downloaded grubconf and it recognized hdb as a Windows partition so I set it up in the menu.  But when I try to boot, it says something like (going from memory)
```

rootnoverify (hd1,0)
makeactive
chainloader +1

```
Then it grinds to a halt and does nothing.  Incidentally, I'm having trouble getting my second HD mounted properly in Kubuntu, but I don't know if this has anything to do with my GRUB problems or not.

Thanks in advance,
kenquad

---

### Post by Sutekh on 2006-01-19
Well settings GRUB to load the Windows install first should be pie, but if it is grinding to a halt, then there may be more to it.

Could you post the output of 
```
sudo fdisk -l
```which will show all your partitions
and
paste your /boot/grub/device.map and menu.lst, which will show where the paritions are and how to run them.

---

