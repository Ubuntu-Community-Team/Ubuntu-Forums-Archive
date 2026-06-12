---
title: "one quick linux find command question"
date: 2009-05-29
forum: General Help
---

### Post by yoma819 on 2009-05-29
hello all
i am trying to do the following
find all jpeg files and then copy them to a specific lication
i have tried this:
find /root/mount/60 "*.jpg" -exec cp /root/mount/16/aaa
all i get is find: missing argument to -exec
help please what am i doing wrong?
--yoma

---

### Post by ActiveFrost on 2009-05-29
Wouldn't it be easier to do it in this way ?

```
cp 'find /root/mount/60/ -name "*.jpg"' /root/mount/16/aaa/
```

---

### Post by unutbu on 2009-05-29
This will copy the jpgs into /root/mount/16/aaa:

```
find /root/mount/60 -name "*.jpg" -exec cp {} /root/mount/16/aaa \;

```
or 

This will copy and preserve the permissions,ownership,timestamps and subdirectory structure:
```
rsync -avm --include='*.jpg' -f 'hide,! */' /root/mount/60/ /root/mount/16/aaa/
```

---

