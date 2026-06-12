---
title: "Missing hard disk space"
date: 2009-05-09
forum: General Help
---

### Post by ultranoize on 2009-05-09
Disk Usage Analyzer tells me that the total file system capacity is 12.5GB but when I scan the file system a usage of 100% is stated corresponding to 7GB. Where are my other 5.5GB?  attached a screenshot of Disk Usage Analyzer [http://dl.getdropbox.com/u/302629/Baobab.png](http://dl.getdropbox.com/u/302629/Baobab.png)

---

### Post by Peter09 on 2009-05-09
Try the terminal command
```
df -h
```

---

### Post by ultranoize on 2009-05-09
This is what I get:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              13G   12G  689M  95% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  344K  504M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2,8M  502M   1% /dev
tmpfs                 505M  1,5M  503M   1% /dev/shm
lrm                   505M  2,0M  503M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1              35G   30G  5,1G  86% /media/sda1
/dev/sda2             3,9G  3,5G  473M  89% /media/sda2
overflow              1,0M  1,0M     0 100% /tmp

```

sda3 is where I have ubuntu installed.

---

