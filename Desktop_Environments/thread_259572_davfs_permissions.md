---
title: "davfs permissions"
date: 2006-09-17
forum: Desktop Environments
---

### Post by dc2447 on 2006-09-17
An old story with [K]Ubuntu

I have davfs setup like this in fstab

[http://www.someserver.com/tango](http://www.someserver.com/tango) /media/webdav davfs user,noauto 0 0

> davidcam@dave-kubuntu:/var/log$ ls /media/webdav/ | wc -l
ls: /media/webdav/: Operation not permitted
0
davidcam@dave-kubuntu:/var/log$ sudo ls /media/webdav/ | wc -l
126
davidcam@dave-kubuntu:/var/log$



I'm a member of the users group and have setuid on mount.davfs


Any ideas other than not use the davfs2 from the repositories?

---

### Post by dc2447 on 2006-09-18
bump

---

