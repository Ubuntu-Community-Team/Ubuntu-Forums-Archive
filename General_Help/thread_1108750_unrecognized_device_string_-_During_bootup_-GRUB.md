---
title: "unrecognized device string - During bootup -GRUB"
date: 2009-03-28
forum: General Help
---

### Post by itkamaraj on 2009-03-28
Hi all,

I am getting this error "unrecognized device string" while i try to enter into ubuntu via grub loader.

Once i choose the ubuntu 8.10 and press enter it shows this error message.

It is happening the recovery mode also.

I tried this solution.

1) boot-up in live cd.
2) sudo grub
3) root (hd6,0)
filesystem type is ext2fs
4) setup (hd0)

checking if "boot/grub/stage1" exists... yes
checking if "boot/grub/stage2" exists... yes
.....
,.....
....


Again i rebooted the system. and now also i am getting the same error.

Can any one help me.

thanks
kamaraj.s

---

### Post by pastalavista on 2009-03-28
I would recommend, instead of a lot of mucking around in the root terminal, that you should download and burn a [SuperGrub Disk]("http://www.supergrubdisk.org/"). It is a simple, automatic grub installer/fixer. There are other ways to do it, but SuperGrub is much easier.

---

### Post by itkamaraj on 2009-04-01
anyway i reinstalled my ubuntu.


This error happened after i installed QGRUBEditor

If anything happened next time, then i will try your solution

thanks
kamaraj.s

---

