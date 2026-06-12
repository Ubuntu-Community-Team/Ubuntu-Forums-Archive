---
title: "Can't use desktop(pic added)"
date: 2007-11-17
forum: Desktop Environments
---

### Post by staar2 on 2007-11-17
All time if i want add something to desktop i get errors and then they don't display icons. But if i use File Browser there i see my desktop files. I hope you understand my problem.

[http://img81.imageshack.us/img81/1623/screenshotfy8.png](http://img81.imageshack.us/img81/1623/screenshotfy8.png)

---

### Post by bingoUV on 2007-11-17
can you give the output of the following commands : 
```

ls -ld ~
ls -ld ~/Desktop
ls -l ~/Desktop

```

---

### Post by staar2 on 2007-11-17
[PHP]
drwxr-xr-x 29 risto risto 4096 2007-11-17 18:42 /home/risto
risto@lauaarvuti:~$ ls -ld ~/Desktop
drwxr-xr-x 2 risto risto 4096 2007-11-17 12:42 /home/risto/Desktop
risto@lauaarvuti:~$ ls -l ~/Desktop
total 1436
-rw-r--r-- 1 risto risto  69392 2007-11-17 11:10 5665.ods
-rw-r--r-- 1 risto risto 245760 2007-11-17 12:42 5665.xls
-rw-r--r-- 1 risto risto  39914 2007-11-17 11:46 57063-Moomex.tar.gz
-rw-r--r-- 1 risto risto 990112 2007-11-17 12:27 Screenshot.png
-rw-r--r-- 1 risto risto 105472 2007-11-17 11:00 test.doc

[/PHP]

---

