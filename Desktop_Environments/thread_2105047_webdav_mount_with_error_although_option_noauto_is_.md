---
title: "webdav mount with error although option noauto is set"
date: 2013-01-15
forum: Desktop Environments
---

### Post by xtrailrunner on 2013-01-15
I have defined an entry in /etc/fstab to mount a webdav drive:
[https://www.myserver.com](https://www.myserver.com) /content/webdav/community davfs   user,rw,noauto  0       0

Although the option is set to noauto I get an error message during boot:
ubuntu an error occured while mounting press S to skip or M to ...
Any ideas why this happens ?

---

### Post by xtrailrunner on 2013-01-15
Solved: There was a space inside the mountpoint (I changed the originally mount point slightly in the post because it is a company server). The only way I found was using \040 to replace the space.

---

