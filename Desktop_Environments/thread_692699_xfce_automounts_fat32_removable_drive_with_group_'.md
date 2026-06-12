---
title: "xfce automounts fat32 removable drive with group 'root'"
date: 2008-02-10
forum: Desktop Environments
---

### Post by Sir.Babau on 2008-02-10
Hi all,

I have a 160 gig external HDD formatted as fat32 and I'm running Xubuntu. When it automounts the files are owned by my user, however they're assigned to the group "root" with the permissions as follows:

rwx------

Whereas I'd like it to be assigned to my user's group and:

rwxrwxrwx

I've gotten it to do that with the following line in fstab:

UUID=47AE-80A3 /media/REDBRICK vfat users,iocharset=utf8,umask=000 0 0

However whenever it mounts from this it's very slow to index the directories on it. ie: I plug it in and the first time I browse the files in Thunar it takes forever to display anything. This problem doesn't occur when there's no fstab entry and the drive is automounted.

Any ideas?

---

