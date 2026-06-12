---
title: "KTorrent 2.0rc1 Install Issue"
date: 2006-07-18
forum: Desktop Environments
---

### Post by eXCeSS on 2006-07-18
```
andrew@linux-laptop:~$ sudo dpkg -i ktorrent_2.0rc1-1_i386.deb
(Reading database ... 117996 files and directories currently installed.)
Unpacking ktorrent (from ktorrent_2.0rc1-1_i386.deb) ...
dpkg: error processing ktorrent_2.0rc1-1_i386.deb (--install):
 trying to overwrite `/usr/share/mimelnk/application/x-bittorrent.desktop', which is also in package kdelibs-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 ktorrent_2.0rc1-1_i386.deb

```

On kubuntu 6.06 using the .debs.
Any help?

edit: used the ,deb from [http://dev.bit-freaks.net/apachelogger/deb/ktorrent/and](http://dev.bit-freaks.net/apachelogger/deb/ktorrent/and) it worked.

---

