---
title: "Issue with compiz (libscale) after update kernel to 4.4.0-59-generic"
date: 2017-01-11
forum: Desktop Environments
---

### Post by cvgaviao on 2017-01-11
Hi all, 

today I run the automatic update that installed kernl to 4.4.0-59-generic and suddenly the compiz started to misbehave.

I can't use the scale anymore and also I can't click in an icon with multiple instances on the launcher nor can't use hot corners. If I do then compiz crash and restart.

looking at the log:

```

Jan 11 20:52:42 cvgaviao-Inspiron-5537 kernel: [14196.606095] compiz[9398]: segfault at 48 ip 00007fc0b49d9cf0 sp 00007ffed3f4b708 error 4 in libscale.so[7fc0b49c7000+25000]
Jan 11 20:53:13 cvgaviao-Inspiron-5537 kernel: [14227.615915] compiz[12124]: segfault at 48 ip 00007f12375d2cf0 sp 00007ffcc5406318 error 4 in libscale.so[7f12375c0000+25000]
Jan 11 20:53:22 cvgaviao-Inspiron-5537 kernel: [14236.835826] compiz[12157]: segfault at 48 ip 00007fdaac9d9cf0 sp 00007fff150944b8 error 4 in libscale.so[7fdaac9c7000+25000]
Jan 11 20:53:27 cvgaviao-Inspiron-5537 kernel: [14241.534229] compiz[12185]: segfault at 48 ip 00007fcc4a5d2cf0 sp 00007ffea52b3658 error 4 in libscale.so[7fcc4a5c0000+25000]
Jan 11 20:53:31 cvgaviao-Inspiron-5537 kernel: [14246.069037] compiz[12208]: segfault at 48 ip 00007f90265d2cf0 sp 00007ffeda289c48 error 4 in libscale.so[7f90265c0000+25000]
J
Jan 11 22:36:08 cvgaviao-Inspiron-5537 kernel: [ 6094.422528] compiz[3194]: segfault at 48 ip 00007f9cdc42ecf0 sp 00007ffd6d890a18 error 4 in libscale.so[7f9cdc41c000+25000]



```

what should I do ?

thanks

---

### Post by cvgaviao on 2017-01-14
Last night I decided to try create another user account. it surprise me that there was no issue while using it.
So, using this new user account I've renamed the problematic older account home folder, then created another one using the same name. After that I just copy the important folders into the new account.
all issues gone and I kept all my user related data (bookmarks, keys, ongoing torrent downloads, etc) !!!

---

### Post by katian on 2017-03-31
solved for me with "sudo apt install --reinstall ubuntu-desktop"

---

