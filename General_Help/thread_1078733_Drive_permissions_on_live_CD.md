---
title: "Drive permissions on live CD"
date: 2009-02-23
forum: General Help
---

### Post by marioliveira on 2009-02-23
Hi. I am using live CD 8.1. I connected USB drives which were recognized, one of them being an external drive which has been formatted in linux ext3 filsystem (it belongs to a Linksys NSLU2 network storage). When I try to copy a file from it to another drive it does not allow me, I think because I do not have permissions to access its files. How can I change permissions (using the live CD) in the ext3 external drive so that I can access and copy from (and also to) it?

---

### Post by taurus on 2009-02-23
Open a terminal and run

Applications -> Accessories -> Terminal
```
gksudo nautilus
```
Now, you should be able to move/copy files to anywhere you want.

---

### Post by marioliveira on 2009-02-23
Terminal gives me back the following>
ubuntu@ubuntu:~$ gksudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized
** (nautilus:8287): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

and I keep being unable to copy files

---

