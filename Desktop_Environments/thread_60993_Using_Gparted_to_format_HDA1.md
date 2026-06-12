---
title: "Using Gparted to format HDA1"
date: 2005-08-30
forum: Desktop Environments
---

### Post by scottishparrothead on 2005-08-30
Okay - a little history:

I'm currently dual-booting Windows XP and Ubuntu.

For some reason my Windows installation has screwed up and I can't reinstall it using my original XP disk (BSOD when I try to install).  I've therefore decided Ubuntu is going to be the sole OS on my laptop.  However, as things stand I've got 30GB of NTSC formatted hard-drive as HDA1 that's virtually useless.

I've downloaded Gparted and want to get rid of HDA1 and format it for linux storage.  However, I'm concerned about overwriting GRUB and not being able to boot at all.  Is this likely?  Where is Grub stored?  Will reformatting destroy the mbr?

More information available on request.

Thanks

Mike

---

### Post by frodon on 2005-08-30
Don't worry about that, you can easily restore your [GRUB](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore) .

Good formating  ;-)

---

### Post by arnieboy on 2005-08-30
[QUOTE=scottishparrothead]Okay - a little history:

I'm currently dual-booting Windows XP and Ubuntu.

For some reason my Windows installation has screwed up and I can't reinstall it using my original XP disk (BSOD when I try to install).  I've therefore decided Ubuntu is going to be the sole OS on my laptop.  However, as things stand I've got 30GB of NTSC formatted hard-drive as HDA1 that's virtually useless.

I've downloaded Gparted and want to get rid of HDA1 and format it for linux storage.  However, I'm concerned about overwriting GRUB and not being able to boot at all.  Is this likely?  Where is Grub stored?  Will reformatting destroy the mbr?

More information available on request.

Thanks

Mike[/QUOTE]
no u wont overwrite grub if u format the NTFS partition because in all probability your grub resides on the MBR (master boot record) which remains untouched even if u format any partition.
the grub configuration file is */boot/grub/menu.lst*
read it and let me know if u have any questions.

---

