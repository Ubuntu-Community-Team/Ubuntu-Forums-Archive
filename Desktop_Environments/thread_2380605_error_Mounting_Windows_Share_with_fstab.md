---
title: "error Mounting Windows Share with fstab"
date: 2017-12-19
forum: Desktop Environments
---

### Post by giobaxx on 2017-12-19
I' m trying to mount permanently a Windows Share through the fstab and basically i have added this line to the file

```
//192.168.0.100/backup$  /home/username/Share/winShare cifs  credentials=/home/username/.smbcredentials,iocharset=utf8,sec=ntlm,uid=1000   0 0
```

Basically seem to work, i see the share and i can create folder or file, but during the boot i see this error;

  [B] [20.978283] CIFS VFS: cifs_mount failed w/return code = -101

[/B]What could be wrong???

---

