---
title: "smbmount ignores uid. Why?"
date: 2005-12-20
forum: General Help
---

### Post by matw on 2005-12-20
$ sudo smbmount //NEWTON/mat /mnt/mat -o username=mat uid=mat gid=mat

mounts the //NEWTON/mat share, but all the files are owned by root and the gid is root. Why does smbmount ignore the uid and gid options?

If, however, I make smbmnt SUID root, as described [here]("http://www.ubuntuforums.org/showthread.php?t=88247&page=2") (thanks Hypatia2), then the command (run as mat)

$ smbmount //NEWTON/mat /mnt/mat -o username=mat uid=mat gid=mat

retains the ownership of the files as intended. Mounting as mat is kind of a work around. I would like to see smbmount work as documented in the man page.

---

