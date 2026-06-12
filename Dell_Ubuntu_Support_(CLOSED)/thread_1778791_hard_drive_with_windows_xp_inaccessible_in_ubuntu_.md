---
title: "hard drive with windows xp inaccessible in ubuntu 10.10 sata/ide combo"
date: 2011-06-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jombo_777 on 2011-06-09
hi,
 
i have a dell gx270 tower with 4 hdd (2 sata) + (2 ide) 
 
order: 
 
ubuntu on 1st sata 80 Gb and working fine
storage on 2nd sata 320 Gb 
win xp on 1st ide 40Gb
win7 on 2nd ide 30Gb
 
in ubuntu only the 80 320 and 30 GB drive can mount
 
the 40Gb one sends me a error saying already mounted but no where to be found???

---

### Post by cariboo on 2011-06-09
Open a terminal and type:

```
df -h
```

The above command will give you a listing of all the mounted partitions.

---

### Post by jombo_777 on 2011-06-10
jonathan@jonathan-desktop:~$ df -h
Sys. de fich.            Taille  Uti. Disp. Uti% Monté sur
/dev/sdc1              36G  8,9G   25G  27% /
none                  1,5G  276K  1,5G   1% /dev
none                  1,5G  344K  1,5G   1% /dev/shm
none                  1,5G  376K  1,5G   1% /var/run
none                  1,5G     0  1,5G   0% /var/lock
/dev/sdb1              29G  9,8G   19G  34% /media/30win7
/dev/sdd1             6,1G  432M  5,7G   7% /media/swap
/dev/sdd2              13G   65M   13G   1% /media/c:\temp
/dev/sdd3             280G  192G   89G  69% /media/jonathan


the missing drive should be ''sda'' ???

if i try to mount it in the disk utility manager i get this message:
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdc1 is already mounted on /
mount failed

---

