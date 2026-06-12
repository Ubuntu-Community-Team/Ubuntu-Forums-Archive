---
title: "bootloader repair"
date: 2006-06-12
forum: Desktop Environments
---

### Post by mbgb14 on 2006-06-12
I just (mistakenly) installed Windows Vista. I had Dapper installed as well. I know for a fact its still there, although Windows Vista overwrote my bootloader, and its now impossible to get to it. How can I restore the bootloader without having to reinstall dapper?

---

### Post by Ramses de Norre on 2006-06-12
Look [here]("http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_reinstall_the_Grub_using_the_Live_CD").

---

### Post by mbgb14 on 2006-06-12
[QUOTE=Ramses de Norre]Look [here]("http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_reinstall_the_Grub_using_the_Live_CD").[/QUOTE]
Didn't work. It said succeded and it all looked great. I rebooted, to see the good ol' "Windows Boot Loader" wtf?

---

### Post by mbgb14 on 2006-06-12
I guess actually there were errors

```
grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0,5)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,5) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub>

```

---

