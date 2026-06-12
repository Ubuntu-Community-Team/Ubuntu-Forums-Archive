---
title: "Steam wants execute permissions on my network share, but it should have it!"
date: 2017-01-30
forum: Gaming &amp; Leisure
---

### Post by duke-wellington on 2017-01-30
Hello. I installed Steam on my Ubuntu 16.04 LTS. I have a network share where I'm trying to place a Steam Library and this is the error I get when I try to add it to the network share:
[https://i.imgur.com/RK4IofN.png](https://i.imgur.com/RK4IofN.png)

I should note that the network share is hosted on Windows Server 2012 R2, and here are the permissions for that:
[http://i.imgur.com/npHD6DI.png](http://i.imgur.com/npHD6DI.png)

Also, here is my /etc/fstab entry:

```
#CIFS share on FILESERVER[FONT=Consolas]
[/FONT]//<My Share IP>/Data    /home/offensive/Media/data  cifs    credentials=/home/offensive/.fileservercredentials,noserverino,auto,uid=1000,gid=1000,user,exec,file_mode=0770,dir_mode=0770,rw 0   2
```

I verified that I actually have execute permissions by doing an ls -la on my share directory:

```
offensive@Offensive-Ubuntu:~$ ls -la Media/data/
total 24
drwxrwx--- 2 offensive offensive  4096 Jan 16 23:41 .
drwxrwxr-x 1 offensive offensive     8 Jan 16 23:36 ..
drwxrwx--- 2 offensive offensive     0 Jan  3 17:23 Programs
drwxrwx--- 2 offensive offensive     0 Jan 17 00:07 Storage
-rwxrwx--- 1 offensive offensive 17920 Nov  4 20:58 Thumbs.db
```

---

### Post by wildmanne39 on 2017-01-30
*Thread moved to **Gaming & Leisure for better support**.*

Please use thumbnails or url's when posting images because many people have slow or limited connections.

---

