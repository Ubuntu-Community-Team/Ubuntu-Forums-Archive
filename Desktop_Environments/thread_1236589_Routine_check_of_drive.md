---
title: "Routine check of drive"
date: 2009-08-10
forum: Desktop Environments
---

### Post by AmerNewbieInDE on 2009-08-10
i got a problem. when i boot my notebook, ubuntu wants to run a routine disk check. 

It shows:

Routine check of drives: /dev/sdb1

58% (stage 1/5, 1929/2316)

then everything is frozen, i cant esc. out of it. i must hold power till it shuts down. What is it cecking.. the 1929 is that files? folders? blocks, sectors what? i think the drive might have bad sectors on it, but they are at the end. i have also looked for a partion manager to chance the partition but i cant find one installed.

cann anyone help?

---

### Post by Raffles10 on 2009-08-10
Partition manager: [GParted]("http://gparted.sourceforge.net/") it's in the repo's.

You can disable the automatic checking of drives in fstab, at the end of your fstab entry you'll see a number, usually 2 for non root partitions, change it to 0.

You can also manage automatic disk checking with: [AutoFsck]("https://wiki.ubuntu.com/AutoFsck") which gives you the option of checking your drives at shutdown rather than at startup.

---

### Post by AmerNewbieInDE on 2009-08-10
thanks for the reply and info, is 0 for boot partitions? because this is my boot drive, i am using an usb external sata drive to run ubuntu. maybe i should have mentioned that.

---

### Post by Raffles10 on 2009-08-10
If /dev/sdb1 is your boot partition you should leave auto disk checking enabled, just manage when it occurs using AutoFsck.

---

### Post by AmerNewbieInDE on 2009-08-10
well, i got gparted.. am i not allowed to change the partition size??every command is greyed out

---

