---
title: "How do I access my Windows hard drive in Ubuntu?"
date: 2006-01-14
forum: General Help
---

### Post by jeff-- on 2006-01-14
Hey everyone, I am wanting to be able to access my hard drive for windows on Ubuntu.  Under disk manager the hard drive name is sda1.  I tried just changing the access path in disk manager but that didn't work.  Can someone link me somewhere that explains this, or tell me how to do this?  I searched the wiki and these forums and I didn't see any results for what I was looking for.

---

### Post by adwait on 2006-01-14
Try this:
[http://easylinux.info/wiki/Ubuntu#Windows](http://easylinux.info/wiki/Ubuntu#Windows)

---

### Post by aysiu on 2006-01-14
[http://www.psychocats.net/linux/mountwindows.php](http://www.psychocats.net/linux/mountwindows.php)

---

### Post by marvlus on 2006-01-14
You have to mount your drives before you can look at them.  try reading this tutorial, it should help:
 [http://www.linux.org/lessons/beginner/l13/lesson13d.html](http://www.linux.org/lessons/beginner/l13/lesson13d.html)

---

### Post by jeff-- on 2006-01-14
Thanks, that helped a lot!

---

### Post by YaseenKriel on 2006-11-09
i used these instructions to access my windows drive but they appear to be for IDE drives only. i had to modify my hdd entry like this:

/dev/sdb1	/media/windows ntfs nls=utf8,umask=0222 0 0

using sdb1 since i am using a SATA drive.

---

### Post by Athanasius on 2006-11-09
```
sudo mkdir /media/windows 
sudo cp /etc/fstab /etc/fstab_backup sudo gedit /etc/fstab
```

Append the following line at the end of file:

```
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0
```

---

### Post by locke.dragon on 2007-03-27
simple, yet effective.  :D

[http://technical-itch.co.uk/2006/11/06/how-to-access-your-windows-hard-drive-from-ubuntu/](http://technical-itch.co.uk/2006/11/06/how-to-access-your-windows-hard-drive-from-ubuntu/)

---

### Post by Gina on 2007-03-27
Doesn't work for me :( Doesn't like the "umask".  

> gina@gina-desktop:/mnt$ sudo mount -t ntfs /dev/sda1 /mnt/windrive -o &#8220;umask=022&#8243;
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

gina@gina-desktop:/mnt$ dmesg | tail
... snip ...
[17199428.188000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17199496.476000] NTFS-fs error (device sda1): parse_options(): Invalid umask option argument: 0222s
[17199552.372000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[17199552.628000] NTFS volume version 3.1.
[17199552.792000] NTFS volume version 3.1.
[17201008.944000] NTFS-fs error (device sda1): parse_options(): Unrecognized mount option &#8220;umask.
gina@gina-desktop:/mnt$



Wonder if it's for 6.10 and not 6.06.

Any ideas please?

---

### Post by locke.dragon on 2007-03-27
sorry.  i'm a n00b.  it worked for me, but sadly, i can't give you any more advice.

---

