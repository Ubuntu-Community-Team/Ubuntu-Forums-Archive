---
title: "What Are The Default Folder Permissions?"
date: 2009-03-28
forum: General Help
---

### Post by umechanism on 2009-03-28
Long story short - I goofed up my folder and file permissions by playing around, resetting them, etc...bad mistake.  Lesson learned.  Now I'm having various problems with programs not launching and files not being written when "saved".  Namely, Firefox will not launch without going to a temainal and typing "sudo firefox".

Anyway - I screwed up.

My question is this - What are the default folder permissions for all the top level folders in Ubuntu?

Thanks!

---

### Post by umechanism on 2009-03-28
> **umechanism said:**
> Long story short - I goofed up my folder and file permissions by playing around, resetting them, etc...bad mistake.  Lesson learned.  Now I'm having various problems with programs not launching and files not being written when "saved".  Namely, Firefox will not launch without going to a temainal and typing "sudo firefox".

Anyway - I screwed up.

My question is this - What are the default folder permissions for all the top level folders in Ubuntu?

Thanks!

I forgot to list my permissions for the top level folder (root). I went to terminal and coded:

"cd /"
"ls -l"

which returned:

michael@ubuntu-dell:/$ ls -l
total 84
drwxr-xr-x   2 root root  4096 2009-03-13 13:43 bin
drwxr-xr-x   3 root root  4096 2009-01-29 22:50 boot
lrwxrwxrwx   1 root root    11 2008-12-24 16:10 cdrom -> media/cdrom
drwxr-xr-x  16 root root 14840 2009-03-28 01:22 dev
drwxr-xr-x 139 root root 12288 2009-03-28 09:14 etc
drwxr-xr-x   4 root root  4096 2009-01-19 22:57 home
lrwxrwxrwx   1 root root    33 2009-01-28 06:12 initrd.img -> boot/initrd.img-2.6.27-11-generic
lrwxrwxrwx   1 root root    32 2008-12-24 16:54 initrd.img.old -> boot/initrd.img-2.6.27-9-generic
drwxr-xr-x  16 root root 12288 2009-02-13 07:17 lib
drwx------   2 root root 16384 2008-12-24 16:10 lost+found
drwxr-xr-x   3 root root  4096 2009-03-27 23:46 media
drwxr-xr-x   4 root root  4096 2009-03-14 23:28 mnt
drwxr-xr-x   3 root root  4096 2009-02-02 21:40 opt
dr-xr-xr-x 173 root root     0 2009-03-27 19:44 proc
drwxr-xr-x  18 root root  4096 2009-03-28 01:10 root
drwxr-xr-x   2 root root  4096 2009-02-18 06:38 sbin
drwxr-xr-x   2 root root  4096 2008-10-29 18:53 srv
drwxr-xr-x  12 root root     0 2009-03-27 19:44 sys
drwxrwxrwt  17 root root   440 2009-03-28 09:16 tmp
drwxr-xr-x  12 root root  4096 2008-12-24 16:23 usr
drwxr-xr-x  15 root root  4096 2008-10-29 19:12 var
lrwxrwxrwx   1 root root    30 2009-01-28 06:12 vmlinuz -> boot/vmlinuz-2.6.27-11-generic
lrwxrwxrwx   1 root root    29 2008-12-24 16:54 vmlinuz

Does this match the Ubuntu's default permissions?

Tks!

---

