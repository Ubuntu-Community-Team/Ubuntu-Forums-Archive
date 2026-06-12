---
title: "Being part of group &quot;root&quot;?"
date: 2009-06-24
forum: General Help
---

### Post by blur xc on 2009-06-24
I've been doing a lot of reading on permissions, and I saw somewhere someone made themselves a member of the "root" user group.  What does that mean, and what powers does it give you?  How is that different than logging in a root, or having, in M$ lingo, admin privileges all the time?

Thanks,
BM

---

### Post by Bachstelze on 2009-06-24
That's a stupid thing to do. When a group has the same name as a user, it should only contain that user as a member. And to answer your question, no, being a member of the root group does not grand you all the prvileges of user root:

```
firas@iori ~ % ls -l /
total 22
drwxr-xr-x   2 root root 2672 2009-06-24 13:51 bin
drwxr-xr-x   4 root root 1024 2009-06-11 14:49 boot
lrwxrwxrwx   1 root root   11 2008-04-10 13:12 cdrom -> media/cdrom
drwxr-xr-x  15 root root 3560 2009-05-11 21:27 dev
drwxr-xr-x   3 root root   80 2009-06-16 00:43 emul
drwxr-xr-x 103 root root 6120 2009-06-25 00:41 etc
drwxr-xr-x  10 root root 4096 2009-02-06 18:38 home
drwxr-xr-x   2 root root   48 2008-02-14 13:13 initrd
lrwxrwxrwx   1 root root   30 2009-05-11 21:24 initrd.img -> boot/initrd.img-2.6.29-2-amd64
drwxr-xr-x  11 root root 4760 2009-06-25 00:41 lib
lrwxrwxrwx   1 root root   20 2009-06-16 00:43 lib32 -> /emul/ia32-linux/lib
lrwxrwxrwx   1 root root    4 2008-04-10 14:24 lib64 -> /lib
drwx------   2 root root   48 2008-02-14 13:11 lost+found
drwxr-xr-x   3 root root   72 2008-10-30 10:04 man
drwxr-xr-x   3 root root   96 2008-02-14 13:12 media
drwxr-xr-x   2 root root   48 2006-10-28 16:07 mnt
drwxr-xr-x   2 root root   48 2008-12-31 15:48 opt
dr-xr-xr-x 127 root root    0 2009-05-11 21:27 proc
drwx------   8 root root  496 2009-06-23 01:33 root
drwxr-xr-x   2 root root 3360 2009-06-24 13:51 sbin
drwxr-xr-x   2 root root   48 2008-09-16 09:22 selinux
drwxr-xr-x   3 root root   72 2009-02-20 07:29 srv
drwxr-xr-x  12 root root    0 2009-05-11 21:27 sys
drwxrwxrwt   7 root root  360 2009-06-25 00:43 tmp
drwxr-xr-x  10 root root  288 2009-06-16 00:43 usr
drwxr-xr-x  16 root root  368 2008-05-01 16:23 var
lrwxrwxrwx   1 root root   27 2009-05-11 21:24 vmlinuz -> boot/vmlinuz-2.6.29-2-amd64

```

Here, you can see that members of the root group have read-only permissions on everything, just like everyone else. Only the root user has write permissions.

---

### Post by blur xc on 2009-06-24
Oh...  I was confused...  I'm still reading all the linux and ubuntu books I can find, and I kind glazed over the users/group/everyone else section.  Well, maybe not glazed, but I didn't study it well enough to know it at the time, but I guess it's time to re-read that section.

I forgot there were three levels of permissions, user-group-everyone else...  

Is it possible to give a file the permission 000 (if I recall right), and make it so not even the root user has access to it?  If you did, is that file permanently locked?

BM

---

### Post by Bachstelze on 2009-06-24
> **Barna Madau said:**
> 
Is it possible to give a file the permission 000 (if I recall right), and make it so not even the root user has access to it?  If you did, is that file permanently locked?

Nope. The root user has access to everything, even things that are chmodded to 000 (there are ways to prevent even the root user from accessing files, using SELinux or AppArmor, but those are more advanced topics).

---

