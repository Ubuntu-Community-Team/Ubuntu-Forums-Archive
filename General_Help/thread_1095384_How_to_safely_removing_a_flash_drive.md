---
title: "How to safely removing a flash drive?"
date: 2009-03-13
forum: General Help
---

### Post by Mythology on 2009-03-13
I have no problems using my usb flashdrive with Ubuntu (which is great because I've been reading about other people having problems with this.)

But my questions is, how do I safely remove my flash drive? For example, on WinXP I right click the drive and click safely remove. A window pops up and I click CLOSE, and then it tells me I can now remove the flash drive.

What about on Ubuntu? Does this have something to do with "mount" and "unmount?" I really am not sure what these words mean and I'm afraid of ruining my system and partitions somehow if I mess with these settings.

Do you just pull the flash drive out when you're done using it?
I just want to be safe. ;)

---

### Post by athaki on 2009-03-13
Right click on the flashdrive and choose unmount. That is the same as 'safely removing' it in xp

---

### Post by viljun on 2009-03-13
If you don't write or change anything - just plug it out.

... oh, wait. This is what i do, but do anyone know if this really is safe or not?

---

### Post by athaki on 2009-03-13
relatively safe, but it's always better to err on the safe side and unmount it first.

---

### Post by Sjeti on 2009-03-13
If you felt fancy and wanted to do it in command line, you'd first need a directory and know what /dev/ it is.

You can find out what your drives are by 

sudo fdisk -l

You can find your drive there, and I'll use my mount directory for example:

```

mount /dev/sdc1 /media/#FFFFFF 

```

Keep in mind you need to have the folder there already to mount it.  If you are having problems mounting it, or the drive was improperly removed you can add:

```
-o force
```

to the end of command.  You can also mount .iso and related files with the -o loop option.

To unmount you use the 'umount' command, not unmount.  You can specify the dev directory or the mount directory, it doesn't matter.

---

