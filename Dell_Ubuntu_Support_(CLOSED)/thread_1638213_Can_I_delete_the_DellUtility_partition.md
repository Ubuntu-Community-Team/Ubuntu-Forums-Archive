---
title: "Can I delete the DellUtility partition"
date: 2010-12-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aeronutt on 2010-12-05
I have multiple OS's that I can boot to (10.04 LTS, Mint 10, and Windows XP). I'm resizing some disk partitions and moving a few things around, and would like to know if I can delete the "DelUtility" partition on my hard disk. It's currently /dev/sda1, fat16, and about 80MB.

And if I do delete it, will Windows XP still boot, and will grub work ok? Any other possible problems with deleting DelUtility, other than not have the Del diagnostics?

Here's a list of the files & dirs in the partition:

AUTOEXEC.BAT  CONFIG.BTS  COPYUP.BAT   DELLDIAG.INI  DIR.LST    SEAL.INI
AUTOEXEC.UP   CONFIG.SYS  DELL         DELLRMK.BIN   HIMEM.SYS
COMMAND.COM   CONFIG.UP   DELLBIO.BIN  diags         SEAL.EXE

---

### Post by gbrainin on 2010-12-05
AFAIK the Dell utility partition is solely a self-contained hardware diagnostics system.  Deleting it should therefore have no effect on anything else, except of course that you won't be able to use the hardware diagnostics.  YMMV, of course.

---

### Post by aeronutt on 2010-12-31
Ok, I'm finally getting around to deleting the dell partition, however, I have a basic question. Here's the output of fdisk -l

/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        2687    21503002+   7  HPFS/NTFS
/dev/sda3            4512       19457   120053683    f  W95 Ext'd (LBA)
/dev/sda4            2688        4511    14651280   83  Linux
/dev/sda5            5234        7145    15358140   83  Linux
/dev/sda6            4512        5233     5799402   82  Linux swap / Solaris
/dev/sda7            7146       19457    98894732   83  Linux

The Dell Utility partition is /dev/sda1 . The last time I deleted a partition, I'm pretty sure it reordered everything after that partition. So, if I delete /dev/sda1, and it reorders/renames all the /dev's after that, will that cause a problem? Will grub work, and still be able to boot?

---

### Post by gbrainin on 2010-12-31
It depends.  If all references in the grub configuration files, as well as /etc/fstab are by UUID, then it won't matter what partition number is assigned.  If, however, you reference partitions by number (such as /dev/sda4) then you'll have to change those to match any new numbering after you repartition.

You can use a live CD or USB to see the numbering scheme and edit the relevant files.

---

### Post by kgarbutt on 2010-12-31
Deleting that partition may mean that you won't be able to recover your computer in a crash if you are still interested in Windows working. My son deleted his HP partition and he wasn't able to recover his computer. He had to purchase a recovery disk from HP. Check to see if you have an option to make recovery disks. & do that before you delete it.

---

### Post by gbrainin on 2011-01-01
Dells typically come with two "extra" partitions: the DellUtility partition is a suite of hardware tests.  There is a separate system restore partition which, as you say, should not be deleted unless a) you have an alternate means of restoring, or b) you understand you are giving up the option of restoring.

Note that the OP said the partition in question was about 80 MB.  This is consistent, since the restore partition is typically in the GB range.

---

### Post by aeronutt on 2011-01-01
Thanks for the caution and help guys, I've loaded XP into virtual box, so I know I have the CD's I need to reload/restore windows. I checked all the grub files I could find, and saw references to only UUID's, no /dev/sda*.  So...I'm going to make sure my liveCD works, and then delete the Dell Utility partition.

---

### Post by aeronutt on 2011-01-01
All went well, thanks for help!  Marked solved.

---

