---
title: "Fstab?"
date: 2006-07-23
forum: Desktop Environments
---

### Post by Rayston on 2006-07-23
anybody want to help me with fstab? my secondary drive is getting mounted as noexec, but I cant find noexec in the fstab, here is a pastebin of the pertinent info, [http://paste.ubuntu-nl.org/18736](http://paste.ubuntu-nl.org/18736)  can anyone help me?

---

### Post by scxtt on 2006-07-23
try using:
```
/dev/sda1       /mount/sda1   ext3           defaults                        0       2
```if you're just looking to get it mounted ...

also, have you tried to mount it from the command line?
[indent]sudo mount -t ext2 /dev/sda1 /mount/sda1[/indent]

---

