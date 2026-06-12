---
title: "CD Writer permissions with Breezy"
date: 2005-10-24
forum: Desktop Environments
---

### Post by Deniel on 2005-10-24
Hello all,
I want to use Gnomebaker for cd burning but with Breezy, the default permissions for users are the following :
daniel@ubuntu:~$ ls -l /dev/hdc
brw-rw----  1 root cdrom 22, 0 2005-10-24 11:57 /dev/hdc

I can change them with 
daniel@ubuntu:~$ sudo chmod o+w /dev/hdc

but I have to do it after each new start of Breezy.

What can I do th have these permissions by default ?
daniel@ubuntu:~$ ls -l /dev/hdc
brw-rw--w-  1 root cdrom 22, 0 2005-10-24 11:57 /dev/hdc

Deniel

---

### Post by mykey on 2005-10-25
just add the user 'daniel' to the 'cdrom' group in /etc/groups

---

