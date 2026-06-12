---
title: "changing mountpoint for CDs?"
date: 2005-08-07
forum: Desktop Environments
---

### Post by orzechowskid on 2005-08-07
hi,

I'm looking to change the directory where removable media is mounted to.  Currently they go in /media  (/media/cdrom, media/floppy, etc.) and I'd like them to be in /mnt .  I tried symlinking the /media directory to point to /mnt , but that broke a lot of things; nothing would show up on the desktop, and I had to be superuser to mount/unmount.

I'm not too clear on what to edit to make this work (a hald config file, maybe?), so any help would be greatly appreciated.  Thanks in advance.

- Dan

PS this is my first problem so far after installing Hoary.  It's a very welcome change from the headaches I had dealing with FC4.

---

### Post by allans on 2005-08-07
You need to edit /etc/fstab, which contains all the settings used to mount your devices including cd drives and floppy drives.  So to get your cd drive mounted on /mnt/cdrom, you would have to change

/dev/hdc    /media/cdrom

to

/dev/hdc    /mnt/cdrom

Unless you have a good reason though, I'd leave them as they are because gnome typically only looks in /mount for devices, at least in hoary this was the case.

Allan

---

### Post by orzechowskid on 2005-08-07
man, I'm an idiot.  I could've sworn I already changed that, but I took a look and I hadn't.  thanks for your help.

(and I need my devices there because some binaries I took home from work make assumptions about where certain files will be.)

---

### Post by allans on 2005-08-07
No problem, glad I could help!

Allan

---

### Post by riks on 2008-07-24
As an alternative to changing the mount point, you can use a symbolic link in order to get a desired path:

ln -s /media/floppy /mnt/floppy

/mnt doesn't seem to be used for mounting temporary storage on my 8.04 machine. I assume you can use that directory as you desire.

---

