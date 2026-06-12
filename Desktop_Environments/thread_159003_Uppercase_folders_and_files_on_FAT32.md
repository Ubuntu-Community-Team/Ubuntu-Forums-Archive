---
title: "Uppercase folders and files on FAT32?"
date: 2006-04-12
forum: Desktop Environments
---

### Post by johso on 2006-04-12
Hiya folks!

So, this is something that has bothered me since... always. But now I've decided to do something!
Whenever I try to make a file or a folder with uppercase letters only, I get two files/folders - one called 'untitled folder' and one with the name I've given it in **lowercase** letters. And mostly I have to 'sudo rm -r <file/folder name>' to delete it again.
What is up with that?
It's generally needed for bands like D-A-D. I ripped and old album of mine yesterday (by D-A-D), and then this problem popped right up again - the folder name being d-a-d. I don't know why, but I just think that looks messy! ;-)
Now, I have got my suspicion directed on the UTF8 encoding, since this warning pops up at bootup (when entering 'verbose' mode):
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

Now, I've read that this is normal, but I still believe it's the cause.
Is there anything I can do about this? 
Thanks in advance, Johs

---

### Post by dcstar on 2006-04-12
[QUOTE=johso]
.......
Now, I have got my suspicion directed on the UTF8 encoding, since this warning pops up at bootup (when entering 'verbose' mode):
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

Now, I've read that this is normal, but I still believe it's the cause.
Is there anything I can do about this? 
Thanks in advance, Johs[/QUOTE]
Native DOS/FAT filesystems are case-insensitive, if you mount them in a non-recommended way then you get strange things occurring.

What is your fstab entry?

---

### Post by johso on 2006-04-12
It looks like this:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda5         /media/fat32      vfat	iocharset=utf8,umask=000	0

---

### Post by dcstar on 2006-04-13
[QUOTE=johso]It looks like this:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda5         /media/fat32      vfat	iocharset=utf8,umask=000	0[/QUOTE]
Mine is:
```
/dev/hda1       /c		vfat    	umask=000,noatime,auto			0       0
```
and it seems to work fine with all file operations.

---

### Post by johso on 2006-04-13
Tried it out - but it doesn't make any difference though.
If you create a folder called 'FOLDER' on your fat32 partition, what will then happen?
Because here, as I've said before, it'll make 2 folders with the same name in uppercase and lowercase, and then remove the one with uppercase letters automatically.

---

