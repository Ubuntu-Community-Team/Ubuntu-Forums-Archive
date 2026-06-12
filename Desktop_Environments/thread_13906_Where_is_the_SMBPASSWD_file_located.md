---
title: "Where is the SMBPASSWD file located?"
date: 2005-02-03
forum: Desktop Environments
---

### Post by istoyanov on 2005-02-03
I configured Samba according to the Unofficial Ubuntu Starter Guide, but after doing
```
 $ sudo smbpasswd -a my_system_username 
``` I didn't find the ``smbpasswd'' (no, not the binary) file that should keep the newly created Samba password.

Is this perhaps a bug in Samba, or am I looking at the wrong place:

> 
--with-privatedir=directory

    Specifies the directory in which Samba keeps the smbpasswd, secrets.tdb, and related files for authentication. The default is /usr/local/samba/private.


I would be thankful for any opinions shared:)

Cheers!

---

