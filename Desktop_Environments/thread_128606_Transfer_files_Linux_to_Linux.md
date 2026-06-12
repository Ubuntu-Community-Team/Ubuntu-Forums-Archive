---
title: "Transfer files Linux to Linux"
date: 2006-02-11
forum: Desktop Environments
---

### Post by namit on 2006-02-11
Maby silly question 

but how do i transfer files from on linux computer to another?

i know windows to linux is samba or winscp but linux to linux i can use ftp but wondering is there another way?

---

### Post by cwaldbieser on 2006-02-11
[QUOTE=namit]Maby silly question 

but how do i transfer files from on linux computer to another?

i know windows to linux is samba or winscp but linux to linux i can use ftp but wondering is there another way?[/QUOTE]
If you install the open-ssh server, you can use scp or sftp to transfer files.  You can also set up NFS (network file system) which is like samba file sharing, but it is *NIX-only.

---

### Post by namit on 2006-02-11
Thanks for that

---

### Post by GeneralZod on 2006-02-12
[QUOTE=cwaldbieser]If you install the open-ssh server, you can use scp or sftp to transfer files. [/QUOTE]

Even better is KDE's fish:// protocol :)

---

