---
title: "Hard Drives are full, bypass 5% reserve"
date: 2009-06-02
forum: General Help
---

### Post by jbrown96 on 2009-06-02
I have a 1TB hard drive that I need to sync about 20GB to, and I think that I'm up against the 5% superuser reserve. I checked the mount manpage and couldn't find any related options. How do I disable it? Ext4


Thanks.

---

### Post by Linteg on 2009-06-02
```
tune2fs -m reserved-blocks-percentage device
```
There you go.

tune2fs works with ext4 even though the man page only mentions ext2 and ext3.

---

### Post by jbrown96 on 2009-06-02
Thanks that worked. Unfortunately it didn't solve my problem. It seems to be something wrong with the file itself, which is strange since I can still open it... but can't copy it.

---

