---
title: "&quot;Computer&quot; Menu"
date: 2005-05-04
forum: Desktop Environments
---

### Post by markr on 2005-05-04
When I open up the "Computer" option in the panel,  I get my CD/DVD, Filesystem and any plugged in USB drives.

What I also want to show here is my /media/c and /media/d drivers (WinXP NTFS and FAT32 partitions respectively).

I can get to these by going up into the root directory and into /media,  but it would be nice to see them immediately.

Mark.

---

### Post by Xerampelinae on 2005-05-04
Well it's slightly inelegant, but I think if you make links to them in /mnt/ then they will appear.

```

mkdir /mnt/c
ln -s /media/c /mnt/c

```

Or you could make the /mnt/c, /mnt/d, /mnt/blah directories and change /etc/fstab to mount your stuff there by default.

---

### Post by jcooper on 2005-05-04
You need to either add these as "Places", then access them via the Places menu, or make sure those drives are in your fstab, and your user account has full permissions to them. If the latter is true, the Computer window will also list those drives.

---

### Post by vassie on 2005-05-11
I have mounted my second hard drive (/dev/hdb) to /media/storage, however it does not show in Computer

I have also checked that /media/storage has permission 777

Ben

---

### Post by UbuWu on 2005-05-11
How can you add things to the places menu?

---

### Post by Alexander Kirillov on 2005-05-11
[QUOTE=markr]When I open up the "Computer" option in the panel,  I get my CD/DVD, Filesystem and any plugged in USB drives.

What I also want to show here is my /media/c and /media/d drivers (WinXP NTFS and FAT32 partitions respectively).

I can get to these by going up into the root directory and into /media,  but it would be nice to see them immediately.

Mark.[/QUOTE]
 This is becoming a FAQ....

See
[http://ubuntuforums.org/showthread.php?t=27087](http://ubuntuforums.org/showthread.php?t=27087)
and
[https://bugzilla.ubuntu.com/show_bug.cgi?id=7641](https://bugzilla.ubuntu.com/show_bug.cgi?id=7641)

---

