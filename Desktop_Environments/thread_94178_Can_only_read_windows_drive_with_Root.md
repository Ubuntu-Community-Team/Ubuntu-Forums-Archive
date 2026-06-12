---
title: "Can only read windows drive with Root?"
date: 2005-11-23
forum: Desktop Environments
---

### Post by TheIdiotThatIsMe on 2005-11-23
The windows drive seems mounted by default by Gnome, with it labeled hda1. However, I can only view the contents of the drive with Root, and when I try to change the permissions I get an error that it's a read only disk and the permissions cant be changed. Is there a way to get around this so I can view the contents with my regular user?

---

### Post by frodon on 2005-11-23
I guess your partition is NTFS and you should know that there's no reliable write support for NTFS for the moment and that's why your partition is read-only.
The only file system which allow a full write/read support with both OS is FAT32 for the moment.

---

### Post by GeneralZod on 2005-11-23
This should help:

[http://ubuntuforums.org/showthread.php?t=91048&highlight=ntfs+root](http://ubuntuforums.org/showthread.php?t=91048&highlight=ntfs+root)

The poster above me is also correct in saying that NTFS support is effectively read-only under Linux.

---

### Post by aysiu on 2005-11-23
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

