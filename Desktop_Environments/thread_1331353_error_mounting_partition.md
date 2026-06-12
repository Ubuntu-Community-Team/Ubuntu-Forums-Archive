---
title: "error mounting partition"
date: 2009-11-19
forum: Desktop Environments
---

### Post by geek11 on 2009-11-19
when i try to automount my parttion using fstab i had this error msg :

> Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

and when i leave this partition from fstab i can mount it but with a password 
and i wish mount automatically lile before without typing the password every time

---

### Post by JustinR on 2009-11-19
I'm sure theres an option under System>Administration>Users and Groups (Click unlock to make changes button if needed)>Click your username>Properties>User Privileges.

---

### Post by geek11 on 2009-11-20
following your method i have granted my user all the privilegies but the error still exist :(

---

### Post by geek11 on 2009-11-22
i have removed the old policy kit  but the error still exist

---

### Post by grizzler on 2009-11-22
That's an NTFS partition, right? What's the line in fstab used to mount it?

---

### Post by noravanq on 2010-04-21
Hi, I have the same problem. I created an Ubuntu Live-USB and installed Ubuntu on my laptop, but after the installation when I plug in that Flash drive, it gives me that exact mounting error.  It tries to mount it as 

```
/dev/sdc1
```

The corresponding line in /etc/fstab/ is 

```

/dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```
when I erase that line from /etc/fstab, it mounts the flash drive all right, except it doesn't show the drive on the desktop, as it does on my other computer. How can I fix that?

Thanks.

---

### Post by vsb004 on 2011-08-19
[SIZE=3]I am using lucid and i am new to linux
One of my drive was also not mounting 
So i Checked which device is it,it was [COLOR=RoyalBlue]/dev/sd7[/COLOR] ,Then

**Opened**[/SIZE][SIZE=3][COLOR=Blue] /etc/fstab[/COLOR][/SIZE][SIZE=3] and [COLOR=DarkOrange]deleted[/COLOR] a line like
"[COLOR=RoyalBlue]/dev/sd7     none[/COLOR]'

and then **opened** [/SIZE][SIZE=3][COLOR=Blue]/etc/mtab[/COLOR][/SIZE][SIZE=3] then [COLOR=DarkOrange]copied[/COLOR] the line of [COLOR=RoyalBlue]/dev/sd5[/COLOR]
[COLOR=DarkOrange]pasted[/COLOR] above it and [COLOR=Sienna]changed [COLOR=RoyalBlue]sd5 to sd7[/COLOR][/COLOR]

and guess what now my drive is listed [/SIZE]:D

---

