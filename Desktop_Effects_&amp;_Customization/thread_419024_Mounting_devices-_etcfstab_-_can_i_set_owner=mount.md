---
title: "Mounting devices- /etc/fstab - can i set owner=mounter?"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by tacubuntuforums on 2007-04-22
Hi:

When I mount a block device, let's say a floppy, there are several options that configure the access permissions on the mounted filesystem, according to its type. Two of them are  uid and gid , to set the owner and group of the files in the file system. Well... I want to know is if there's a way I can configure the file: /etc/fstab  so that same user that does the mounting becomes the owner of the files in the mounted system, each time.  Because, specially, when using floppies, it's absurd that all users know the root's password or that they need to write the mounting command with the loooong uid and gid options so that they are the owners of the files in the mounted filesystem.

I've read that for some filesystem types, by default or by putting uid within the options but without value, you can make the owner of the files to be the process. But I've tried it and it doesn't work. Even if I'm the owner of the process "mount", it's root, and not me, the owner of the mounted files.

Thanx

---

### Post by Rinzwind on 2007-04-22
Cdroms are set that way ;) 

See /etc/fstab
/dev/scd0       /media/cdrom0   udf,iso9660 **user**,noauto     0    

More info here:
[http://www.linuxquestions.org/linux/answers/Hardware/etc_fstab_broken_down_and_explained](http://www.linuxquestions.org/linux/answers/Hardware/etc_fstab_broken_down_and_explained)

---

### Post by tacubuntuforums on 2007-04-22
Rinzwind:

Maybe I wasn't clear enough. The option user, doesn't work. At least for me. It allows anybody, not only the superuser to mount the device. But still, the owner of the files in the mounted filesystem is root and not the user who mounted it.

---

### Post by yabbadabbadont on 2007-04-22
Edit: never mind, you already covered my suggestion in your initial post.  (which I clearly did not read closely enough...)

---

### Post by tacubuntuforums on 2007-04-22
It seems quite natural with floppies. Just imagine a library, or a class room where, obviously, every student wants to be the owner of the filesystem in his own diskettes and mount them in the twinkling of an eye.

---

### Post by tacubuntuforums on 2007-04-23
There must be a common, well known, way to do it but I still can't figure it out.
Any more ideas?

---

### Post by eyelessfade on 2007-04-23
the "user" flag will indeed mount as the user. Just not for a readonly medium such as a cdrom. Just try for yourself using a usb-stick or something similar. I just did to verify.

---

### Post by tacubuntuforums on 2007-04-26
OK eyelessfade and all:
Now I understand. My mistake was that I was using a floppy formated with ext3 (a grub boot floppy).
When mounting a FAT formated floppy, the mounter becomes the owner. It's ok
With cdroms it the owner is root, which also seems the reasonable option to me.

---

