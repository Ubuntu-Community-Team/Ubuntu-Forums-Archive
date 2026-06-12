---
title: "Changing ownership of devices"
date: 2011-01-08
forum: Desktop Environments
---

### Post by Fracta on 2011-01-08
I have a hard drive that I want to set permissions for, but it never lets me. For example, there is a pagefile.sys and I want to set the owner to root to make sure it is never touched, but I can't do it, even with the terminal.
This is the first step towards getting a folder that only particular users can access, that is also shared on the local network but still password protected, so the same users can access it from a different pc. 
Sorry if this is in the wrong place,  its not really a networking question yet.
Thanks for your help

---

### Post by nomko on 2011-01-08
> **Fracta said:**
> I have a hard drive that I want to set permissions for, but it never lets me. For example, there is a pagefile.sys and I want to set the owner to root to make sure it is never touched, but I can't do it, even with the terminal.
This is the first step towards getting a folder that only particular users can access, that is also shared on the local network but still password protected, so the same users can access it from a different pc. 
Sorry if this is in the wrong place,  its not really a networking question yet.
Thanks for your help


[SIZE=2]
Try this:
[/SIZE][SIZE=2]**[COLOR=#0000ff]sudo chmod -R 777 /media/***[/COLOR]**[/SIZE]

Where *** is the device name (i.e. sda1 or sdb1) or label (see the folder /media which label the drive has).

---

### Post by Krytarik on 2011-01-08
Judging from the "pagefile.sys" you are apparently talking about a FAT or NTFS filesystem. You cannot apply linux permissions to those filesystems, at least not for specific files/directories, only partition-wide through the mount options.

Greetings.

@nomko: Eh?! :-s

---

### Post by Fracta on 2011-01-09
"You cannot apply linux permissions to those filesystems"
Thank you! That explains everything.

---

