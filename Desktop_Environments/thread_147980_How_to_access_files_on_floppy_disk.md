---
title: "How to access files on floppy disk?"
date: 2006-03-21
forum: Desktop Environments
---

### Post by stig on 2006-03-21
Hi,
In Ubuntu whereabouts in the file browser do I find the files when I insert a floppy disk in the drive? I don't often use a floppy drive and this is the first time I've tried to use it in Ubuntu.

In the file browser I found folders under media called floppy and floppy0 but both are empty although the floppy disk has 4 Word files on it.

If I do Places, Computer, and open Floppy Drive I get "Unable to open selected volume" and the details are:
Warning: device /dev/fd0 is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount

Thanks!

---

### Post by tedius on 2006-03-21
The is a bug in Breezy which prevents it from mounting floppies automatically.  There is a bug report about this and a thread that explains how to fix it. (Unfortunately I can't remember either at the mo.)

A quick way around this is to type the following;
```
mount /media/floppy0
```
If you get an error about only root can mount then append "sudo" to the front of this command.

Once it is mounted a floppy will appear on you desktop and in Nautilus.

Just remember when you are finished to umount it.

Hope this helps.

---

### Post by stig on 2006-03-21
Thanks for the reply. I tried your suggestion but all I get is:

mount: I could not determine the filesystem type, and none was specified"

---

### Post by tedius on 2006-03-21
Ah I forgot about that :) 

Try this;
```
mount -t vfat /dev/fd0 /media/floppy0
```

The "-t vfat" tells it that this disk is formatted with the fat32 format (windows)

/dev/fd0 is the device to mount and /media/floppy0 is the folder to mount it on (ie where you will be able to access the files on the disk)

---

### Post by stig on 2006-03-21
[QUOTE=tedius]Ah I forgot about that :) 

Try this;
```
mount -t vfat /dev/fd0 /media/floppy0
```

The "-t vfat" tells it that this disk is formatted with the fat32 format (windows)

/dev/fd0 is the device to mount and /media/floppy0 is the folder to mount it on (ie where you will be able to access the files on the disk)[/QUOTE]

Thanks for the clarification. Immediately after writing my last reply I carried on looking for info because you said there was a way to fix it. I found this thread:

[http://www.ubuntuforums.org/showthread.php?t=113947&highlight=mount+floppy+breezy](http://www.ubuntuforums.org/showthread.php?t=113947&highlight=mount+floppy+breezy)

with the 3 instructions:

sudo gedit /etc/fstab

under floppy0, changed 'auto' to 'vfat' and saved the change

then sudo mount /media/floppy0 and it showed up in nautilus.

This has allowed me to access my floppy drive and copy files from it.

---

