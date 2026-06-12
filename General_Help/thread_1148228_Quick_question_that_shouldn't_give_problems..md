---
title: "Quick question that shouldn't give problems."
date: 2009-05-04
forum: General Help
---

### Post by Mamsaac on 2009-05-04
What are the default permissions in /usr/lib ?

I made a stupid mistake and changed them =(

---

### Post by tornadof3 on 2009-05-04
On my system they are

```
$ ls -l
total 252
drwxr-xr-x   2 root root 69632 2009-05-03 15:44 bin
drwxr-xr-x   2 root root  4096 2009-04-19 17:35 games
drwxr-xr-x  38 root root  4096 2009-04-19 16:33 include
drwxr-xr-x 209 root root 69632 2009-05-03 15:39 lib
drwxr-xr-x  34 root root 57344 2009-04-23 17:41 lib32
lrwxrwxrwx   1 root root     3 2009-04-19 13:57 lib64 -> lib
drwxr-xr-x  10 root root  4096 2009-04-19 13:57 local
drwxr-xr-x   3 root root  4096 2009-04-19 16:30 man
drwxr-xr-x   2 root root 12288 2009-05-03 15:39 sbin
drwxr-xr-x 338 root root 12288 2009-04-22 21:35 share
drwxrwsr-x   7 root src   4096 2009-04-19 16:36 src
drwxr-xr-x   2 root root  4096 2009-04-19 14:02 X11R6

```

---

### Post by Mamsaac on 2009-05-04
Thanks, that fixed it =)

---

