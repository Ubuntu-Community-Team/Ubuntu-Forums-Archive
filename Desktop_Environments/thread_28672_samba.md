---
title: "samba"
date: 2005-04-21
forum: Desktop Environments
---

### Post by oldforce on 2005-04-21
pls tell me how to browse my network from kubuntu...
i installed samba but how can i see the shares and computers..

---

### Post by dataw0lf on 2005-04-21
```
mount -t smbfs //servername/sharename /whatever/directory/you/want/to/mount/to -o username=windowsusername,password=windowspassword
```

---

