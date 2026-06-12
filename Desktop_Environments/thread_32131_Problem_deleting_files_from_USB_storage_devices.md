---
title: "Problem deleting files from USB storage devices"
date: 2005-05-06
forum: Desktop Environments
---

### Post by Raptor Ramjet on 2005-05-06
I have noticed a problem when using both my USB flash drive and my USB MP3 player with Ubuntu.

The problem is simply that when I delete items from the key they are being placed in a trash folder on the device (named ".Trash-username") However this trash folder does not show up in the wastebasket and emptying the wastebasket does not remove it so, although the files are now logically deleted (i.e. they no longer show up in Nautilus), the space has not been freed on the device.

This is somewhat annoying as it means the only way to actually delete the files (and thereby free up the space) is by opening a terminal and using "rm" to manually remove the files - which is only actually a pain because I can never remember the mount point for the devices... (note to self: "/media/usbdisk"... "/media/usbdisk"... ;)

So whilst it's not a showstopper I don't believe the GNOME wastebasket code is handling USB devices correctly.

---

### Post by az on 2005-05-06
If you tell nautilus to show hidden files and then delete the files in the wastebasket, they are gone.

---

### Post by Domhnull on 2005-05-06
That's what I do.  It'd be nice if SHIFT+DELETE or something like that would remove the files instead of moving them to the trash folder.

---

### Post by jeremy on 2005-05-06
[QUOTE=Domhnull]That's what I do.  It'd be nice if SHIFT+DELETE or something like that would remove the files instead of moving them to the trash folder.[/QUOTE]
 In Nautilus preferences you can add 'Delete' to your options.

---

### Post by Jade Robbins on 2006-02-28
Is there a way to alltogether remove the use of the trash bin? Or in some places make it so that it didnt' use the .Trash-username? I mount windows shares onto my filesystem and the other day someone pointed out that there is alot of .Trash-jaderobbins on them :s

---

