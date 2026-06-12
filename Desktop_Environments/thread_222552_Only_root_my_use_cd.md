---
title: "Only root my use cd"
date: 2006-07-25
forum: Desktop Environments
---

### Post by doomstone on 2006-07-25
I have a little problem with that only my root user are allowed to use the cdrom. how can i do so that all users can use the cdrom drive?](*,)

---

### Post by philippe_carlo on 2006-07-25
Make sure thet the line with 'hdc' in /etc/fstab looks as follows:

```

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by doomstone on 2006-07-25
My shows 
```
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
The only defirint is that it is /dev/hdb

---

### Post by doomstone on 2006-07-25
```
doomstone@doommedia:/media$ dir -l
total 2
lrwxrwxrwx 1 root root    6 2006-07-25 02:26 cdrom -> cdrom0
drwx------ 2  400  401 2048 2006-04-12 08:44 cdrom0
```

---

### Post by philippe_carlo on 2006-07-25
can you do the following:

```

sudo umount /media/cdrom0
mount /media/cdrom0

```

Make sure to run the second comand WITHOUT sudo.

---

### Post by doomstone on 2006-07-25
After i have done that do i still not have access to the cdrom. 
and no i did not use sudo infront of mount

---

