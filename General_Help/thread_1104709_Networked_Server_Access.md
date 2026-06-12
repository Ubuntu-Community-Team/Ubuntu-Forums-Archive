---
title: "Networked Server Access"
date: 2009-03-23
forum: General Help
---

### Post by gamewolf on 2009-03-23
In Windows Server, you are able to access a server drive that appears under My Computer. It appears as if it is a local hard drive, but it is actually on the server.

Is there any kind of server software that would have this kind of feature?

Thanks.

---

### Post by peterLinux on 2009-03-23
Depends on what you want to do.

Either samba or NFS can give you access to networked drives.

PeterLinux

---

### Post by gamewolf on 2009-03-24
Alright, looks like NFS is what i'm looking for. The HowTo in the Community Docs only tell how to setup the client on Ubuntu. Is there a way to connect XP/Vista to a Unix NFS Server? If so, could someone tell me or post a link to a howto?

Thanks.

---

### Post by Iowan on 2009-03-24
NFS is usually Unix-Unix (Linux-Linux), but I'll look around for a Windows package.

---

### Post by gamewolf on 2009-03-24
Ah ok. Thanks!

---

### Post by Iowan on 2009-03-24
[This]("http://ubuntuforums.org/showthread.php?p=6951276") thread claims to have XP accessing NFS files.

---

### Post by peterLinux on 2009-03-24
You need samba on the NFS server... both pointing to the same 'shares' on the harddisk.

Look at FreeNas... it is not based on Ubuntu but it might give you an idea of what is posible
(freenas.org)

---

### Post by gamewolf on 2009-03-25
Its not exactly what I was looking for, but it looks good and easy to use. Thanks.

---

