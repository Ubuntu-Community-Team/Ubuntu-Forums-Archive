---
title: "Loop AES // Harddisk encryption"
date: 2006-06-05
forum: Desktop Environments
---

### Post by Fab on 2006-06-05
Hello!
While using Breezy, I followed the following tutorial ([http://deb.riseup.net/storage/encryption/loop-aes/](http://deb.riseup.net/storage/encryption/loop-aes/)) to install loop-aes and encrypt one partition for sensitive data. The problem is that since upgrading to dapper it doesn't work anymore, probably due to the kernel change(?). I tried to redo it all, but can't remember exactly what the correct package names were (the tutorial uses some old debian ones). Any advice?

Oh yeah, error message when trying to mount the partition is: ioctl: LOOP_SET_STATUS: Invalid argument, requested cipher or key length (240 bits) not supported by kernel

And yeah, I know, stupid me for not backing the stuff up before upgradeing ;P

---

### Post by Fab on 2006-06-07
nothing?

---

### Post by loko on 2006-08-19
I also have had this problem.

The solution of it is to install loopaes-utils from the repos.

---

### Post by loko on 2006-11-07
i have to mention that you have to do the following because just installing the loop-aes-utils is not enough to get the encrypted harddisk to mount.

you have to do:

```
sudo modprobe aes
```
and
```
sudo modprobe cryptoloop
```

---

### Post by Fab on 2006-11-13
Doesn't work for me. What does though is the stuff described in [http://ubuntuforums.org/showthread.php?t=194860&highlight=loop-aes](http://ubuntuforums.org/showthread.php?t=194860&highlight=loop-aes)

---

