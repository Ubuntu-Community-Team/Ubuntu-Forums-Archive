---
title: "How to assign name to external drive?"
date: 2006-02-03
forum: Desktop Environments
---

### Post by anthro398 on 2006-02-03
I've got an external firewire drive that I'd like to name.  I used fdisk and mkfs to prepare it for use, but it doesn't have a name and I have no idea how to do that.  I'd like it to have a name so that automount mounts it to /media/<name> when I plug it in to the system.  Any ideas?  Also, where is that name stored?  MBR?

---

### Post by cwaldbieser on 2006-02-04
[QUOTE=anthro398]I've got an external firewire drive that I'd like to name.  I used fdisk and mkfs to prepare it for use, but it doesn't have a name and I have no idea how to do that.  I'd like it to have a name so that automount mounts it to /media/<name> when I plug it in to the system.  Any ideas?  Also, where is that name stored?  MBR?[/QUOTE]
If you put an ext2 or ext3 filesystem on it, you can use "e2label".  If the filesystem is vfat, I think the program you want to use is called something like "mtools" (for MS-DOS tools), but I am not 100% sure I have the spelling correct.

---

### Post by awi on 2006-02-04
The program you need, if you are trying to name a F.A.T. partition, is [COLOR="DarkGreen"]mlabel[/COLOR], from [COLOR="DarkGreen"]mtools [/COLOR]package.

---

### Post by anthro398 on 2006-02-07
Hey thanks,

I'd have never guessed it was fs type specific, but that makes sense if the name is stored as fs metadata.  Thanks again.

---

