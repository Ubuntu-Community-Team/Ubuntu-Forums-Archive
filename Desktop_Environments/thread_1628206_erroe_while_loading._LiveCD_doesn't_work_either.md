---
title: "erroe while loading. LiveCD doesn't work either"
date: 2010-11-22
forum: Desktop Environments
---

### Post by sledge81 on 2010-11-22
Hello,

I've been trying to fix the problem since the past 6 hours and no clue what's going wrong.

The system was working fine until I switched it off and on.

First I get the initramfs error. I clicked on 'e' when shown the box to choose Ubuntu Generic/Recovery/Memory Test options.

recordfail
insmod part_msdos
insmod ext2
set root="(hd0,msdos1)"
search --no-floppy --fs-uuid --set 0a8540ac-406e-42cd-b2c5-4c7ad90b072
echo "Loading Linux 2.6.35-22-generic ..."
linux /boot/vmlinuz-2.6.35.33-generic root=UUID= 0a8540ac-406e-42cd-b2c5-4c7ad90b072  ro single
echo "Loading initial ramdisk ..."
initrd /boot/initrd.imp-2.6.35-22-generic

When running through the USB, I get the following:

stdin:error 0
/init: line 7: can't open /dev/sr0: No medium found

Please help.

---

### Post by sledge81 on 2010-11-22
Hello..?? Can anyone help me with this issue please?

---

