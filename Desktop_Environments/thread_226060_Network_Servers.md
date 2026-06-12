---
title: "Network Servers"
date: 2006-07-30
forum: Desktop Environments
---

### Post by LookTJ on 2006-07-30
deleting folders in network servers?

i tried deleting a ftp folder/network, it didnt delete

:confused: 

help i installed ubuntu yesterday ;)

thanks in advance

~Taylor

EDIT: here a pic, i tried to delete the one with 192.168.0.102

[[IMG]http://img110.imageshack.us/img110/3274/helpgr6.png[/IMG]](http://imageshack.us)

~Taylor

---

### Post by NotJustANewbie on 2006-07-30
Its probably because you are not logged into the network to delete/modify the files and therefore you don't have sufficient permissions!

Try using gftp to login to Windows networks (which have a ftp server on of course such as FileZilla).

Good luck

---

### Post by LookTJ on 2006-07-30
> **NotJustANewbie said:**
> Its probably because you are not logged into the network to delete/modify the files and therefore you don't have sufficient permissions!

Try using gftp to login to Windows networks (which have a ftp server on of course such as FileZilla).

Good luck

im trying to delete folder...not folders inside it

i meant im trying to delete the folder inside of network servers

Thanks

~Taylor

---

### Post by NotJustANewbie on 2006-07-30
In that case, you must be root.

In terminal, type:
```
sudo nautilus
```
, find network servers, and try deleting again ... In the tabs at top of window (Go -> Network)

---

