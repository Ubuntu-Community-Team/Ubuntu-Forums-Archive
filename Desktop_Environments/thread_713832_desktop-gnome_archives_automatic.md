---
title: "desktop-gnome archives automatic ?"
date: 2008-03-03
forum: Desktop Environments
---

### Post by steph552 on 2008-03-03
Hi,

I discovered that my machine made some backup of my desktop ( I think)
my disk was completely full
and I found into /var/archives, some TAR files, <Username>-desktop-home-<date>.master.tar.gz of 20 to 30 Gb !!!

Any idea where this comes from  ??
and how to get ride of this "backup" ???
As far as I know, I don't have any backup systems  :-(

Thanks

---

### Post by JoseArmandoJeronymo on 2008-07-12
Same here.

And from a first glance it looks like the master.tar.gz file is created almost as large as it takes to make the partition full.

---

### Post by JoseArmandoJeronymo on 2008-07-13
The problem here was caused by package backup-manager which I had installed while looking for a command line ftp utility (which ended up being ftp-update, in case anyone needs one :)).

Apparently backup-manager was trying to create a full backup of my root partition and went as far as there was room for the master.tar.gz files.

This was simple to solve but getting to the answer was only possible because

a. I used this

```
find / -xdev -size +104857600c
```
from [http://www.linuxquestions.org/questions/mandriva-30/root-partition-full-388116/]("http://www.linuxquestions.org/questions/mandriva-30/root-partition-full-388116/") to identify the three backup master tarballs and


b. spotted a mention to backup-manager in messages.log.

---

