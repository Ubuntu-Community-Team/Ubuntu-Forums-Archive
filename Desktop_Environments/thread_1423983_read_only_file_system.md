---
title: "read only file system"
date: 2010-03-07
forum: Desktop Environments
---

### Post by jmsgz on 2010-03-07
as you can see i am trying to chmod so i can delete "evolution-backup.tar.gz" on cdrom0 

here are the file attributes:
dr-xr-xr-x 2 root root 2.0K 2010-03-07 07:18 .
drwxr-xr-x 5 root root 4.0K 2009-10-28 15:55 ..
-r--r--r-- 1 root root   58 2010-03-07 07:18 .checksum.md5
-r--r--r-- 1 root root 698K 2010-03-07 07:16 evolution-backup.tar.gz

i have logged in as root and tried changing attributes

root@xxx-xxxxxxx:/media/cdrom0# chmod +w evolution-backup.tar.gz
chmod: changing permissions of `evolution-backup.tar.gz': Read-only file system

do i need to change the attributes of the drive or what to delete this file?

thanks as usual in advance.
jsg :-)

---

### Post by amauk on 2010-03-07
You can't alter things on a CD
It's read-only (as seen in the error messages)

Even re-writable discs can only be wiped
(as opposed to altered)

---

### Post by webtechquery on 2010-03-07
Hi there.
Well I'm not sure if you are deleting the data from the CD or what. If it is CD-RW then may be you have to format it and then write the data again. And if its not the case of CD, then I would suggest you to check the following web. Though its an article related to other problem, but it also has some chmod rights using tips.

[http://www.webtechquery.com/index.php/2010/02/you-dont-have-permission-to-access-httplocalhost-files-or-folders-on-this-server-in-ubuntu-linux/](http://www.webtechquery.com/index.php/2010/02/you-dont-have-permission-to-access-httplocalhost-files-or-folders-on-this-server-in-ubuntu-linux/)

Hope it works for you.

Thanks.

---

### Post by jmsgz on 2010-03-07
it is a cdrw disk on a cdrw drive. i am simply trying to Delete the file.
:-)

---

### Post by falconindy on 2010-03-07
> **jmsgz said:**
> it is a cdrw disk on a cdrw drive. i am simply trying to Delete the file.
:-)
That's not how rewriteable CDs/DVDs work. You don't get to add/delete at will like a hard drive. You still write in sessions or tracks. If you want to delete something, you need to erase the entire disc.

---

### Post by jmsgz on 2010-03-07
this is a cdrw disk in a cdrw drive so why won't brasero let me blank it? When i ask to blank it in Brasero it says select a disk but the disk is greyed out??? So you can't select it for blanking!!!
:-)

---

### Post by Midnight Star on 2010-03-07
I'm not totally positive here, but if the disc has been finalized will it still allow writing new sessions? Also, it might depend on which system did the initial writing. Unless it uses the same format or standard, it probably won't allow another (the software than didn't do the original writing) to modify it.

---

