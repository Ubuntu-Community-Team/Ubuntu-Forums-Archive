---
title: "How do I copy my VMWare Virtual Machine with SCP"
date: 2009-01-31
forum: General Help
---

### Post by 11235 on 2009-01-31
I am running VMWare on my Ubuntu laptop and I want to backup my existing Windows XP Virtual Machine directory on my laptop to a headless Ubuntu file server for safe keeping.  I am trying to copy the VM directory as follows:

me@ubuntu-laptop:~$ scp /var/lib/vmware/"Virtual Machines"/ root@userver:Public_Share/Virtual_Machines

When I try this I get the following error:

/var/lib/vmware/Virtual Machines: not a regular file

This is my first post.  I would appreciate any help with SCP or any suggestions on how I need to backup my VM's in the future.  I will be creating other VM's I would like to archive also.

Thanks in advance.

---

### Post by HermanAB on 2009-01-31
You could use scp -r, but I always make a tar ball of the VM subdirectory first, then copy the tar file and untar on the other side.

$ sudo tar -zcvf windoze.tgz /where/ever/it/is/windoze

Cheers,

Herman

---

### Post by 11235 on 2009-01-31
I'll try that. Thanks!

---

