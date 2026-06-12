---
title: "Changing User Permission on NTFS partition"
date: 2006-02-23
forum: Desktop Environments
---

### Post by gsplsngr on 2006-02-23
I can play mp3 that are loaded on ipod shuffle but can't play them from my NTFS partition...Tried to copy mp3 over to linux partition, but could not view it from my login


was told I needed to do this 

```
sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

```
and then this 

and then add the following at the end of the page:
Code:

```
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
```

where hda1 would be the partition where you have NTFS..now this may vary on your system so please check before adding it.

But I don't know where to put 

```
/dev/hda1 /media/hda1 ntfs umask=0222 0 0 ?

```


Here is the what information I am getting.


```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 vfat defaults 0 0
/dev/hda2 /media/hda2 ntfs defaults 0 0
/dev/hda6 /osshare vfat defaults 0 0
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
```

---

### Post by Mustard on 2006-02-23
Just looking at your /etc/fstab above it appears your ntfs drive is /dev/hda2.  Basically you need to edit the line in your /etc/fstab that refers to /dev/hda2 to this...

```
/dev/hda2/   /media/hda2  ntfs  nls=utf8,umask=0222 0 0
```

This is the line you want to change below (in bold)

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 vfat defaults 0 0
**/dev/hda2 /media/hda2 ntfs defaults 0 0**
/dev/hda6 /osshare vfat defaults 0 0
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

It should look like this after editing...
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /media/hda1 vfat defaults 0 0
/dev/hda2/   /media/hda2  ntfs  nls=utf8,umask=0222 0 0
/dev/hda6 /osshare vfat defaults 0 0
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
```

---

### Post by Mustard on 2006-02-23
I notice you have two fat partitions as well that need to be set up for access by the user as well. :)

For the fat partitions you should substitute these values (below) for the current value of 'defaults'...

```
iocharset=utf8,umask=000
```

This would change your current lines for fat partitions to...

```
dev/hda1 /media/hda1 vfat iocharset=utf8,umask=000 0 0
```
```
/dev/hda6 /osshare vfat iocharset=utf8,umask=000 0 0
```

---

### Post by aysiu on 2006-02-23
After you edit your /etc/fstab, you may want to reboot your computer.

If you prefer not to, type these two commands: ```
sudo umount /dev/hda2
sudo mount -a
```

---

### Post by Mustard on 2006-02-23
[QUOTE=aysiu]After you edit your /etc/fstab, you may want to reboot your computer.

If you prefer not to, type these two commands: ```
sudo umount /dev/hda2
sudo mount -a
```[/QUOTE]

Hehehe..woops...I should have thought about that, but I got lost in the detail. :)  Thanks for finishing the process for me. ;)

---

### Post by gsplsngr on 2006-02-23
Hot Dog!!!! It Worked\\:D/

---

### Post by Mustard on 2006-02-23
[QUOTE=gsplsngr]Hot Dog!!!! It Worked\\:D/[/QUOTE]

Thats good news.  Well done.

---

