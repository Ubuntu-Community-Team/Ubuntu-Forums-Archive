---
title: "Need help with identifying distribution"
date: 2005-08-22
forum: Desktop Environments
---

### Post by ::DoGG:: on 2005-08-22
Hello guys, i have a little problem. 
I have a system at work. It was installed by previous sysadmin and i have no clue how to touch this stuff. Basically the mounts look like this:
```

rootfs on / type rootfs (rw)
/dev/root on / type ext3 (ro)
/proc on /proc type proc (rw)
/dev/hda1 on /sysdrv type ext3 (rw)
/dev/loop0 on /etc type ext3 (ro)
/dev/loop1 on /var type ext3 (rw)
/dev/pts on /dev/pts type devpts (rw)
/dev/shm on /dev/shm type tmpfs (rw)

``` 

As You can see the /etc is mounted as read only so i cant`t even change the root password, i can`t mount it again in rw mode cause when the system is running the etc is in use and i really want to avoid restarting the system cause it`s pretty important corporate gateway.

So guys.
1. Is there another way to change the root password ?
2. Is there a way to remount /etc in rw mode without rebooting ?

P.S. Here is a main directory structure, the system and kernel are in the sysdrive directory, here are the contents:
```

drwxr-xr-x    4 root     root         4096 Sep 21  2003 .
drwxr-xr-x   10 root     root         1024 Sep 11  2003 ..
-rw-r--r--    1 root     root       527589 Sep 21  2003 System.map
-rw-r--r--    1 root     root          238 Sep 18  2003 bdir100.conf
drwxr-xr-x    2 root     root         4096 Sep 18  2003 boot
-rw-r--r--    1 root     root         7168 Feb 13  2003 boot-text.b
-rw-r--r--    1 root     root       967754 Sep 21  2003 bzImage
-rw-r--r--    1 root     root          800 Feb 13  2003 chain.b
drwxr-xr-x    2 root     root         4096 Sep 18  2003 dev
-rw-r--r--    1 root     root      4194304 Sep 21  2003 etc.disk
-rw-r--r--    1 root     root      4338535 Sep 11  2003 fw.img.gz
-rwxr-xr-x    1 root     root       162564 Aug 20  2003 lilo
-rw-------    1 root     root        64512 Sep 21  2003 map
-rw-r--r--    1 root     root      2097152 Sep 21  2003 var.disk

```
and here is the main directory listing:
```

drwxr-xr-x   10 root     root         1024 Sep 11  2003 .
drwxr-xr-x   10 root     root         1024 Sep 11  2003 ..
drwxr-xr-x    3 root     root         2048 Sep 11  2003 bin
drwxr-xr-x    5 root     root         1024 Sep 18  2003 dev
drwxr-xr-x   13 root     root         1024 Aug  9 14:18 etc
drwxr-xr-x    2 root     root         1024 Sep  8  2003 init
drwxr-xr-x    3 root     root         2048 Sep  9  2003 lib
dr-xr-xr-x   32 root     root            0 Aug  3 08:01 proc
lrwxrwxrwx    1 root     root            3 Sep 11  2003 sbin -> bin
drwxr-xr-x    4 root     root         4096 Sep 21  2003 sysdrv
lrwxrwxrwx    1 root     root            7 Sep 11  2003 tmp -> dev/shm
drwxr-xr-x    6 root     root         1024 Sep 18  2003 var

```

---

