---
title: "Can't put files on external hard drive!"
date: 2009-01-12
forum: General Help
---

### Post by tegnoto89 on 2009-01-12
I'm getting an error saying "the destination is read-only" when I try to put my files on an external hard drive.  How can I fix this?  Thanks in advance!

---

### Post by taurus on 2009-01-12
What filesystem is your external harddrive?  Post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

