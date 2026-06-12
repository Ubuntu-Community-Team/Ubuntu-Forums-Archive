---
title: "What is automounted to tmpfs?"
date: 2013-02-13
forum: Desktop Environments
---

### Post by graysky on 2013-02-13
In reference to [my post](http://ubuntuforums.org/showthread.php?t=2115722) here, can someone running Ubuntu from HDD (not from the LiveCD) please post the output of:

```
mount | grep tmpfs
```
and
```
df -h | grep tmpfs
```

---

### Post by ali abry on 2013-02-14
her is output from ubuntu 12.04.1 with 4G of ram.
```
$ mount | grep tmpfs
udev on /dev type devtmpfs (rw,mode=0755)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)

``````
$ sudo df -h | grep tmpfs
[sudo] password for aliali: 
tmpfs           788M  1.0M  787M   1% /run
aliali@lp:~$ 

```

---

