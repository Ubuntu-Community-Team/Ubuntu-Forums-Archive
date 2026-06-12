---
title: "filesystem suddenly went into read-only"
date: 2009-11-28
forum: Desktop Environments
---

### Post by ikki_72 on 2009-11-28
I don't know what happened, suddenly transmission says my filesystem gone to read-only mode. Have anyone ever got into this situation?

---

### Post by yazmonium on 2009-11-28
The way I fix it is to restart my computer and allow the automatic file system checker run and when it fails and you get a root shell type

fsck -y

and press ctrl-D after it completes.  It takes a long time so don't restart during the check.

---

### Post by dasunst3r on 2009-11-28
If you are running Karmic, there is something that checks on your hard disk's status regularly.  You can find it by going to System -> Administration -> Disk Utility.

---

### Post by ikki_72 on 2009-11-28
thanks. Since the filesystem of my /home directory is reiserfs, i had to use

```
fsck.reiserfs --rebuild-tree /dev/sda3
```

where /dev/sda3 is that /home partition

---

