---
title: "how to change permission on mounted partition"
date: 2009-05-24
forum: General Help
---

### Post by hero1900 on 2009-05-24
i create an ext3 partition and i want to give it permission since i cant do any things with it
is it by chmod for the file in Media folder in the / or what is the correct way
thanks
:)

---

### Post by callan79 on 2009-05-24
> **hero1900 said:**
> i create an ext3 partition and i want to give it permission since i cant do any things with it


Hello hero1900,

Is the partition mounted at the moment?

Can you please post the output of :

```
ls -la /media/
```

Cheers
Callan

---

### Post by hero1900 on 2009-05-24
$ ls -la /media/
total 56
drwxr-xr-x  7 root root  4096 2009-05-25 08:07 .
drwxr-xr-x 21 root root  4096 2009-05-22 20:14 ..
lrwxrwxrwx  1 root root     6 2009-05-20 08:24 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2009-05-20 08:24 cdrom0
drwxrwxrwx  1 root root 16384 2009-05-24 01:51 disk
drwxrwxrwx  1 root root  4096 2009-05-24 01:51 disk-1
drwxrwxrwx  1 root root  8192 2009-05-24 01:52 disk-2
-rw-r--r--  1 root root   354 2009-05-25 08:07 .hal-mtab
-rw-------  1 root root     0 2009-05-25 04:39 .hal-mtab-lock
drwxrwxrwx  1 root root 12288 2009-05-25 05:01 New Volume

---

### Post by callan79 on 2009-05-26
> **hero1900 said:**
> 
drwxrwxrwx  1 root root 16384 2009-05-24 01:51 disk
drwxrwxrwx  1 root root  4096 2009-05-24 01:51 disk-1
drwxrwxrwx  1 root root  8192 2009-05-24 01:52 disk-2
drwxrwxrwx  1 root root 12288 2009-05-25 05:01 New Volume



Hi hero1900,

With the above ones, whichever one is the ext3 one, just do chmod and also chown.

You could try :

```
sudo chown yourusername yourgroupname /media/mountpoint
```

Cheers
Callan

---

