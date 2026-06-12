---
title: "Truecrypt mount permission question"
date: 2009-02-07
forum: General Help
---

### Post by pompiuses on 2009-02-07
I mount my truecrypt volume with the following mount options: 
rw,sync,utf8,uid=1000,umask=0000

This causes all files and directories to have full access for everyone "-rwxrwxrwx", which is bad.

Instead I want everything to be mounted with permission "-rwxr-xr-x". What do the 'uid' and 'umask' mount options have to be to achieve that?

Thanks :-)

---

### Post by pompiuses on 2009-02-07
Looks like umask=0022 did the trick :-)

---

