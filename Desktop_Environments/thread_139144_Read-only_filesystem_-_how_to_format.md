---
title: "Read-only filesystem - how to format"
date: 2006-03-03
forum: Desktop Environments
---

### Post by Vinze on 2006-03-03
Hey, a combination of Windows XP and the school's paranoid system adminstration got my MP3 player messed up, and now I can't write to it anymore. It got my Playlist folder messed up, and now I have a lot of (executable) files with weird characters in their name. I want to format it, but my MP3 player hasn't got such an option. 

How can I either write to it (being root doesn't matter, it still says it's a read-only filesystem) or format it.

Thanks.

---

### Post by el3ktro on 2006-03-03
Plug your MP3 player in, DON'T mount it (or unmount it if it does mount it automatically) and then on the console do "mkfs.vfat /dev/xxx" with xxx being your MP3-players device name.

Tom

---

### Post by Vinze on 2006-03-03
[QUOTE=el3ktro]Plug your MP3 player in, DON'T mount it (or unmount it if it does mount it automatically) and then on the console do "mkfs.vfat /dev/xxx" with xxx being your MP3-players device name.

Tom[/QUOTE]
I got the following error: > $ mkfs.vfat /dev/sda
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: unable to open /dev/sda


Do you happen to know what could be the problem? Thank a lot.

---

### Post by el3ktro on 2006-03-03
/dev/sda is not correct. The MP3 player has one or more (most likely just one) partition, so it must read /dev/sda1. Just do an "ls /dev/sd*" and you'll see all the devices.

Tom

---

### Post by Vinze on 2006-03-03
[QUOTE=el3ktro]/dev/sda is not correct. The MP3 player has one or more (most likely just one) partition, so it must read /dev/sda1. Just do an "ls /dev/sd*" and you'll see all the devices.

Tom[/QUOTE]
That just returns "/dev/sda" and for mounting it has always worked.

---

### Post by el3ktro on 2006-03-03
Oh okay, now I read again over your post. I think you forgot "sudo". Remember everything that somehow affects the system has to be done with sudo!

Tom

---

### Post by Vinze on 2006-03-03
OK, that looks as if it would work, it just returns > $ sudo mkfs.vfat /dev/sda
Password:
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: Will not try to make filesystem on full-disk device '/dev/sda' (use -I if wanted)


Anyway, I'm wondering, if I do this (with -I), will my MP3-player still work?

---

### Post by el3ktro on 2006-03-03
You need the -I switch when you want to format your MP3 player because it doesn't use any partitions at all.

Tom

---

