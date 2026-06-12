---
title: "Can Not login to Wayland Session After Upgrading to Ubuntu 24.10 with GNOME 47.0"
date: 2024-10-12
forum: Desktop Environments
---

### Post by suseno on 2024-10-12
After Upgrading from Ubuntu 24.04.01 to Ubuntu 24.10 tonight.
I can not login on Wayland session —which is the default session—

**However This still works:**
&#128077; Login with Xorg session (the login prompt works)
&#128077; Login using another wayland Desktop Enviroment (I tried Weston)
&#128077; Login with a newly created user

**Suspected *dmesg* output**
```
[ 89.746948] gnome-shell[4032]: segfault at 20 ip 00007a49f79b88fa sp 00007a49c5ffe7d0 error 4 in libmutter-15.so.0.0.0[1b88fa,7a49f7858000+17d000] likely on CPU 3 (core 3, socket 0)
[ 89.746960] Code: ff ff 48 89 c7 48 89 c3 e8 23 b2 ea ff 4c 89 f7 e8 eb 8b ea ff 48 8b 0d 54 56 0b 00 4c 89 ee 48 89 df 48 89 c2 e8 86 fb ea ff <49> 8b 74 24 20 48 89 df e8 c9 ce ea ff 48 89 df 5b 41 5c 41 5d 41
```

I am using X86_64 AMD Ryzen™ 5 5600G CPU and Radeon RX6600 GPU

Has anyone suffer the same problem?

---

### Post by suseno on 2024-10-12
[SIZE=4]**SOLVED**[/SIZE]

I don't know what the heck is the problems.
Since I can login using a newly created user account, I believe the problem is with my current customizations.
It seems that some of my old settings make a segfault on GNOME Shell 47 —Well... I keep my home folder since Ubuntu 8.04 (you read that right, 2008 Ubuntu, 16 years old)—

**The Solution:**
```
$ dconf reset -f /org/gnome/desktop/
```

In case you want to backup your old dconf settings first:
```
$ dconf dump /org/gnome/desktop > dconfbackup.txt
```

Where *dconfbackup.txt* is the filename of your backup.

To restore the backup:
```
$ dconf load /org/gnome/desktop < dconfbackup.txt
```

---

### Post by volteos on 2024-10-17
It might be because Ubuntu LTS right now is on GNOME 46 not 47. Just a guess though.

---

### Post by rhenschel on 2024-11-27
Ubuntu 24.10 is not LTS.  BTW I also have this same problem, but the dconf fix didn't work.   Might also be because this ASUS R500A is an antique...

---

### Post by rhenschel on 2024-12-07
The problem was fixed by new update of libmutter-15.  This went in (from dpkg.log file):
2024-12-06 21:52:54 status unpacked mutter:amd64 47.0-1ubuntu4.1
2024-12-06 21:52:54 status half-configured mutter:amd64 47.0-1ubuntu4.1
2024-12-06 21:52:54 status installed mutter:amd64 47.0-1ubuntu4.1
2024-12-06 21:52:54 configure gir1.2-mutter-15:amd64 47.0-1ubuntu4.1 <none>
2024-12-06 21:52:54 status unpacked gir1.2-mutter-15:amd64 47.0-1ubuntu4.1
2024-12-06 21:52:55 status half-configured gir1.2-mutter-15:amd64 47.0-1ubuntu4.1
2024-12-06 21:52:55 status installed gir1.2-mutter-15:amd64 47.0-1ubuntu4.1

---

