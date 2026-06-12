---
title: "GVFS and Fuse"
date: 2009-01-02
forum: General Help
---

### Post by Timo Laine on 2009-01-02
I am mounting SMB shares with GVFS, but they do not appear under ~/.gvfs/. In Nautilus however they appear normally. I think I have installed all the required packages such as gvfs-fuse, and I do not understand the problem. Could someone help me to begin to resolve the issue?

---

### Post by Timo Laine on 2009-01-03
Apparently the problem was in Ubuntu EEE. The /bin/fusermount program was not setuid root. The solution was

```
sudo chmod u+s /bin/fusermount
```

---

