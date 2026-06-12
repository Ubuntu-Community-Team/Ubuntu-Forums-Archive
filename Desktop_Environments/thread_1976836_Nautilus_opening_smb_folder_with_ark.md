---
title: "Nautilus opening smb folder with ark"
date: 2012-05-09
forum: Desktop Environments
---

### Post by 4thfloorstudios on 2012-05-09
Hi,
I have some problems with nautlius and network shares. Sometimes (not everytime), nautlius opens my network folders (connected via smb and mounted by fstab entry) with ark.

This is very strange, so can anyone help me out?

Additionally sometimes the mount gets lost which is very annoying and there are two links to the share. One with root privileges and one without. I made a symlink to one of the folders which has root privileges but the mount shown in nautlius does not althoug I provided the correct password.

Here is my fstab entry:
```
# nas server share
//192.168.1.103/share /home/oliver/nasserver cifs username=oliver,password=PASSWORD,auto,iocharset=utf8

```

Thank you!

Oliver

---

