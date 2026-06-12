---
title: "can i mount an NTFS hard drive using unix shell ?"
date: 2009-01-24
forum: General Help
---

### Post by ahmed_nasr on 2009-01-24
hey , am trying to learn the unix shell on ubuntu ... I try to mount NTFS hard drive using the mount command : i do :

```
 mount /dev/sdb8
```


and i get :

```
mount: can't find /dev/sdb8 in /etc/fstab or /etc/mtab

```

so what can i do to get this to work ?

---

### Post by SOULRiDER on 2009-01-24
You need to tell it where to mount it. For example
```
mount /dev/sdb8 /media/windows
```
Remember the mount directory has to be created first.

---

### Post by bumanie on 2009-01-24
I usually make a directory to mount to such as > sudo mkdir /mnt/windows then would do something like > sudo mount -t ntfs /dev/sdb8 /mnt/windows

---

### Post by ahmed_nasr on 2009-01-24
thanks guys

---

### Post by Iowan on 2009-01-24
[Here]("http://ubuntuforums.org/showthread.php?&t=283131") is a nice (although involved) **fstab** thread.

---

