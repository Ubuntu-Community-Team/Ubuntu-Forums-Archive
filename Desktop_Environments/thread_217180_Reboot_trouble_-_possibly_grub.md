---
title: "Reboot trouble - possibly grub?"
date: 2006-07-16
forum: Desktop Environments
---

### Post by jackocleebrown on 2006-07-16
Hello,

I've been happily using Ubuntu for the last 8 months or so and have been getting on really well with it.

I have a dual boot XP & Dapper setup on a Acer laptop (Aspire 1800).

I've encountered a strange problem: if I boot into either OS from cold (if the computer has been off for a while) I have no trouble and the correct OS will smoothly start. If I either reboot or restart then the system will hang just after the Grub screen. This happens on both operating systems. To get the computer working again I need to leave it off for about 10 mins before starting it again.

output of "fdisk -l"

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6687    53713296    7  HPFS/NTFS
/dev/hda2            9018        9729     5719140    5  Extended
/dev/hda3   *        6688        9017    18715725   83  Linux
/dev/hda5            9122        9729     4883760    b  W95 FAT32
/dev/hda6            9018        9120      827284+  82  Linux swap / Solaris

I was using GRUB in the MBR to boot both of the operating systems but this weekend to try and fix the problem I moved grub to the boot sector of /dev/hda3 and installed the GAG bootloader in the MBR. It is early days but it looks like this might have cleared up reboot problems when I'm using XP but I still have the same problems with Ubuntu. This makes me think that GRUB might be the cause?

Any help greatfully appretiated - didnt want to leave it to get worse and find myself unable to boot one day!

Thanks, Jack.

---

### Post by jackocleebrown on 2006-07-17
BUmp.

I know this is a tricky one... is there a more appropriate place for me to ask this?

---

