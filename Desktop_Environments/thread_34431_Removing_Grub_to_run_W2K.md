---
title: "Removing Grub to run W2K?"
date: 2005-05-14
forum: Desktop Environments
---

### Post by fredtheman on 2005-05-14
Hello,

Out of curiosity, I added Ubuntu 5.04 on a host running W2K Pro, and set Grub to be run from the MBR. Now that I've taken a look, I no longer need Ubuntu (my mum has no use for it), so would like to restore the W2K boot loader and delete the two partitions (/ and swap). Can I boot with eg. a 98 boot floppy, and type the familiar fdisk /mbr, or should I use a particular boot floppy for W2K?

Thank you
Fred.

---

### Post by Sam on 2005-05-14
You have to boot with your win2k cd. At one point your will be asked to go to recovery mode. Then you'll be in a prompt, and you must use the fixmbr command (if I remember correctly). I don't know if I miss something, maybe someone will correct me.

---

### Post by Euphoric Nightmare on 2005-05-14
you could always go into grub...set the default to win2k, and put the timeout at like 1

---

### Post by bored2k on 2005-05-14
[QUOTE=Euphoric Nightmare]you could always go into grub...set the default to win2k, and put the timeout at like 1[/QUOTE]
 Or just setup grub so it gets hidden by default.

---

### Post by Sam on 2005-05-14
It won't be a complete uninstall with that. The better is to restore the MBR.

---

### Post by Nu-Buntu on 2005-05-15
This would be a good thing for Linux distros to do . . .

1. Make a backup of the MBR upon installation
2. Give the option to restore the MBR backup

This is how well-behaved install routines should work.

---

### Post by fredtheman on 2005-05-15
[QUOTE=Sam]You have to boot with your win2k cd. At one point your will be asked to go to recovery mode. Then you'll be in a prompt, and you must use the fixmbr command (if I remember correctly).[/QUOTE]

Worked like a charm :-) After booting from the CD, choose Repair (R), followed by Console (C), and answer Yes (Y) when asked whether to reinstall the NT MBR.

Thank you
Fred.

---

### Post by equilibrium on 2005-05-15
boot from a dos disk 

fdisk /mbr

 :-#

should re-write the master boot record on the disk. I think there is also a util in recovery mode for restoring mbr.

fdisk /mbr is the very old way :) I remember doing it to remove virus's from the master boot record years ago (win 3.11 + dos 6.22) :)

---

### Post by bored2k on 2005-05-15
[QUOTE=equilibrium]boot from a dos disk 

fdisk /mbr

 :-#

should re-write the master boot record on the disk. I think there is also a util in recovery mode for restoring mbr.

fdisk /mbr is the very old way :) I remember doing it to remove virus's from the master boot record years ago (win 3.11 + dos 6.22) :)[/QUOTE]
 Windows disc does this with fixmbr, but I'd really suggest getting Ultimate boot cd or hiren's v6 for this. Just in case things don't go as expected.

---

### Post by Nu-Buntu on 2005-05-16
fdisk /mbr only works with DOS-based versions of Windows (Windows Me, 98, 95, 3.1, 3.0, and MS-DOS). For NT-based Windows, e.g. 2000, XP, you have to use the recovery console.

---

### Post by equilibrium on 2005-05-27
[QUOTE=Nu-Buntu]fdisk /mbr only works with DOS-based versions of Windows (Windows Me, 98, 95, 3.1, 3.0, and MS-DOS). For NT-based Windows, e.g. 2000, XP, you have to use the recovery console.[/QUOTE]

possibly FAT32 / NTFS difference as 'fdisk /mbr' works for windows xp running on a fat32 drive.

 :-?

---

