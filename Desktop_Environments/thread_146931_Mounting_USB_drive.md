---
title: "Mounting USB drive"
date: 2006-03-19
forum: Desktop Environments
---

### Post by blue_shift on 2006-03-19
I've read all the articles I could find with search, but to no avail.
I'm trying to mount a USB drive. It will mount automatically in Gnome.

I followed the instructions given in another post, and ran mount in gnome.

Then with the information, I tried:
```
alex@home:/media$ sudo mount -t  /dev/sda1  /media/usb type vfat rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8
```

This just returns the help page. Have I malformed the command?

Thanks in advance.

---

### Post by vidak on 2006-03-19
[QUOTE=blue_shift]I've read all the articles I could find with search, but to no avail.
I'm trying to mount a USB drive. It will mount automatically in Gnome.

I followed the instructions given in another post, and ran mount in gnome.

Then with the information, I tried:
```
alex@home:/media$ sudo mount -t  /dev/sda1  /media/usb type vfat rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8
```

This just returns the help page. Have I malformed the command?

Thanks in advance.[/QUOTE]

I think you misunderstood the instructions from that post... :-k  (if you mean USB mount post)
Those lines are for the /etc/fstab file. If you want to edit it, and need more info: man fstab
A sort summary: the first field is what you want to mount, the second tells where, the third is the filesystem's type, the fourth are the mounting options, and the last  two are for dump, and fsck, respectively. 

if you want to mount manually, i.e. you want to enter all the options in command line, you should use
sudo mount /dev/sda1 /media/usb 
maybe with "-o rw,user"
You usually won't need the filesystem type, it's detected automatically. (otherways add "-t vfat" or whatever the fstype is)
That should do it.

Good luck!

---

### Post by blue_shift on 2006-03-19
Thanks, that worked perfectly. I'll be testing the fstab file too. Alex.

---

