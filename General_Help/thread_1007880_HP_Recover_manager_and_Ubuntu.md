---
title: "HP Recover manager and Ubuntu"
date: 2008-12-10
forum: General Help
---

### Post by cta16 on 2008-12-10
I have an HP laptop and instead of a recovery disk, there is a recovery partition. Right now, I have 3 partitions:

1. Vista
2. Recovery
3. Ubuntu

I want to reinstall windows without touching my Ubuntu partition. My question is, if I use the Recover Manager that is on my computer, will it write over my Ubuntu partition too? I know it will probably write over Grub. What can i do to bring Grub back?

---

### Post by plucky on 2008-12-11
> I have an HP laptop and instead of a recovery disk, there is a recovery partition.

I would recommend you backup your recovery partition onto DVD,so you can re-install Windows if your hard  disk breaks.There should be an HP program to do this.

> My question is, if I use the Recover Manager that is on my computer, will it write over my Ubuntu partition too?


No,it should not unless you get it to re-format the whole drive.But that would also remove the recovery partition.Just make sure you specify the correct partition to use.

> I know it will probably write over Grub. What can i do to bring Grub back? 

You can use the Live CD to re-install grub to the MBR.See this [tutorial](http://ubuntuforums.org/showthread.php?t=740221&highlight=grub+mbr)


Good Luck

---

