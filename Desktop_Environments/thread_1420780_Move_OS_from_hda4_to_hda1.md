---
title: "Move OS from hda4 to hda1"
date: 2010-03-03
forum: Desktop Environments
---

### Post by Barriehie on 2010-03-03
Hey all,  so I'm dual boot with 8.04 on hda1, boot partition, and debian on hda4.  I'ld like to copy hda4 to hda1 so that debian resides on the partition I'm booting from, any ideas on the best method?

TIA,
Barrie

---

### Post by Barriehie on 2010-03-03
I'm thinking mount hda1 after booting into hda4 and then:

  1. remove all folders/files on hda1
  3. rsync -vrl hda4 to hda1
  4. edit menu.lst and fstab
  5. reboot

What am I missing?  Anyone have any experience, tips, tricks, hints with this?

TIA,
Barrie

---

### Post by Barriehie on 2010-03-04
Bump, anyone???

---

