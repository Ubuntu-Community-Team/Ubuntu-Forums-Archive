---
title: "Dell Inspiron Duo 1090"
date: 2012-08-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gww6 on 2012-08-23
I finally put a bigger hard drive in my net-book so that I could dual boot Windows 7 and Ubuntu 12.04.  Unfortunately, the Ubuntu installer does not recognize that Windows 7 is already installed.

I used the tried running Ubuntu off of the Live CD.  I ran the ```
sudo os-prober
``` to see what the installer was looking at.  
It returned with ```
/dev/Sda 1: Windows 7 (Loader):Windows:Chain
```
I then tried to remove the dmraid file.  I used ```
sudo apt-get remove -y remove dmraid
```

The computer then returned ```
The following packages will be REMOVED:
dmraid
0upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 139 kB disk space will be freed.
(Reading database... 150247 files and directories currently installed.)
Removing dmraid...
update-initramfs is disabled since running on read-only media
Processing triggers for man-db...
```

The OS-prober did not change after doing this.  Is there anything I am doing wrong.  I unfortunately need windows 7 for a few key programs.  I hope one of you guys are able to help me.

---

