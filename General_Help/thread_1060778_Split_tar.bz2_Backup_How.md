---
title: "Split tar.bz2 Backup How ?"
date: 2009-02-05
forum: General Help
---

### Post by Rodney9 on 2009-02-05
I have backed up my hard drive with Ubuntu 8.10 using -

> tar cvpjf backup.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys /

and I end up with a 8Gb file, it is to big for burning to dvd, so how do I split it into small sizes ?

Rodney

---

### Post by geirha on 2009-02-05
The split command, as the name may suggest, can split files. 
```
split -d -b 4G backup.tar.bz2 backup.tar.bz2.
```
The above should create files backup.tar.bz2.00, backup.tar.bz2.01, backup.tar.bz2.02, etc... that are at most 4 GiB of size.

To put them back together again:
```
cat backup.tar.bz2.* >backup.tar.bz2
```

---

### Post by Rodney9 on 2009-02-06
Thank You

---

