---
title: "Can't mount floppy"
date: 2005-03-06
forum: Desktop Environments
---

### Post by folkers on 2005-03-06
When I try to mount a floppy via Computer>Disks, I get this error message;

mount: I could not determine the filesystem type, and none was specified

When I try to mount /mnt/floppy on the commandline, I get this error message:

mount: can't find /mnt/floppy in /etc/fstab or /etc/mtab

I reinstalled Ubuntu this morning (due to some annoying dual boot problems - it's single boot now) and before the reinstall, everything worked fine. I have tried out three floppies, so it is unlikely that they are all broken. What is the cause and/or solution?

---

### Post by doitashimashite on 2005-03-06
Is there something on the floppy you need?
If so, what filesystem is on the floppy? Is it DOS (FAT) formatted, or ext2/ext3?
If not, use the floppy formatter under Applications / System Tools, to format the floppy using a file system type of choice (DOS or Linux native).

---

### Post by neotool on 2005-03-06
I'm having this problem too. The file system I'm using is FAT.

---

### Post by folkers on 2005-03-06
I'm using the FAT file system. I could work without the data on the floppy, but I put some 3D art on it which I'd like to see back.

---

### Post by doitashimashite on 2005-03-06
My suggestion is to install mtools.
With that, you can do:

$ mdir a:
and
$ mcopy a:* .

I bet that will work; at least you will have your artwork on harddisk, and you could format the floppy after that.

---

### Post by kafton on 2005-03-06
[QUOTE=folkers]When I try to mount a floppy via Computer>Disks, I get this error message;

mount: I could not determine the filesystem type, and none was specified

When I try to mount /mnt/floppy on the commandline, I get this error message:

mount: can't find /mnt/floppy in /etc/fstab or /etc/mtab

I reinstalled Ubuntu this morning (due to some annoying dual boot problems - it's single boot now) and before the reinstall, everything worked fine. I have tried out three floppies, so it is unlikely that they are all broken. What is the cause and/or solution?[/QUOTE]

Look in /etc/fstab and see if your floppy drive is listed (/dev/fd0). If it is not, add it.
Look in /mnt to make sure you have a floppy directory.
Look in /etc/modules to see if "floppy" is in the list of modules - if it is not add it and reboot.

---

### Post by folkers on 2005-03-12
mtools worked great. Thanks for the advice.

---

