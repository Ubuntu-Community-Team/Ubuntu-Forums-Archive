---
title: "Peculiar Boot Issue on Dell Inspirion 1525"
date: 2008-09-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kalmdave on 2008-09-18
I have Dell Inspirion 1525 laptop/notebook  with three partitions. **First partition** has Vista home premium with Hardy heron insatlled inside it and this Hardy Heron is on **second partition** (which means it's not a clean install, right?) the third **partition** has Ubuntu Studio.

Now the Problem,

Hardy heron is not showing up, everytime I select from the menu it tells me:

File: \ubuntu\winboot\wubildr.mbr
Status 0xc0000225

Vista is Loading so is Ubuntustudio.

I  want all three to coexist peacefully :)

---

### Post by Khalis7 on 2008-09-20
> **kalmdave said:**
> I have Dell Inspirion 1525 laptop/notebook  with three partitions. **First partition** has Vista home premium with Hardy heron insatlled inside it and this Hardy Heron is on **second partition** (which means it's not a clean install, right?) the third **partition** has Ubuntu Studio.

Now the Problem,

Hardy heron is not showing up, everytime I select from the menu it tells me:

File: \ubuntu\winboot\wubildr.mbr
Status 0xc0000225

Vista is Loading so is Ubuntustudio.

I  want all three to coexist peacefully :)

It seems that you have an issue with wubi bootloader. Try to google for SuperGrub, download and burn it on a disk. Then try to boot form the SuperGrub cd. What the SuperGrub does is it will repair any problem with grub and even mbr that prevents you from booting into Ubuntu or Windows.

I myself had numerous time being not able to boot into Ubuntu due to some problem with grub but SuperGrub had bailed me out of the problem everytime I need it.

---

### Post by kalmdave on 2008-09-22
@ Khalis7

Thanks, for your prompt answer, i'll surely do that:)

---

