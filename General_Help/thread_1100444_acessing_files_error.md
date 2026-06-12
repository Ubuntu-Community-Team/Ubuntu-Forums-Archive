---
title: "acessing files error"
date: 2009-03-19
forum: General Help
---

### Post by lex1 on 2009-03-19
although news owns this directory it cannot access it what to do?
always get permission denied. 

here is the directory:

total 40
drw-r--r-- 4 news news 4096 2009-03-19 10:35 .
drwxr-xr-x 12 root root 4096 2009-03-19 07:38 ..
-rw-r----- 1 news news 392 2009-03-17 13:40 news.crit
-rw-r----- 1 news news 392 2009-03-17 13:40 news.err
-rw-r----- 1 news news 7782 2009-03-19 10:10 news.notice
drwxrwxr-x 2 news news 4096 2008-12-14 23:51 OLD
drwxrwxr-x 2 news news 4096 2008-12-14 23:51 path
-rw-r--r-- 1 root root 62 2009-03-17 13:40 rc.news

also for this error message:

Log file sizes:
> ls: cannot access /var/log/news/errlog: No such file or directory
> ls: cannot access /var/log/news/news: No such file or directory
> ls: cannot access *.log: No such file or directory
> 4 news.crit  4 news.err  8 news.notice


it news cannot acess these files 
how do i create errlog file and news file as news user bearing in mind news cannot acess this file permission denied?

lex1;)

---

### Post by taurus on 2009-03-19
> **lex1 said:**
> although news owns this directory it cannot access it what to do?
always get permission denied. 

here is the directory:

total 40
**[COLOR="Red"]drw-r--r-- 4 news news 4096 2009-03-19 10:35 .[/COLOR]**
drwxr-xr-x 12 root root 4096 2009-03-19 07:38 ..
-rw-r----- 1 news news 392 2009-03-17 13:40 news.crit
-rw-r----- 1 news news 392 2009-03-17 13:40 news.err
-rw-r----- 1 news news 7782 2009-03-19 10:10 news.notice
drwxrwxr-x 2 news news 4096 2008-12-14 23:51 OLD
drwxrwxr-x 2 news news 4096 2008-12-14 23:51 path
-rw-r--r-- 1 root root 62 2009-03-17 13:40 rc.news

also for this error message:

Log file sizes:
> ls: cannot access /var/log/news/errlog: No such file or directory
> ls: cannot access /var/log/news/news: No such file or directory
> ls: cannot access *.log: No such file or directory
> 4 news.crit  4 news.err  8 news.notice


it news cannot acess these files 
how do i create errlog file and news file as news user bearing in mind news cannot acess this file permission denied?

lex1;)

If you want to access a directory, you need the executable permission, x.

Is that the $HOME directory of user news?

```
sudo chmod 755 .
ls -la
```

---

### Post by lex1 on 2009-03-19
thanks for your post its the log files
in /var/log/news

how do i create
drw-r--r-- 4 news news 4096 2009-03-19 10:35 .


lex1;)

---

### Post by taurus on 2009-03-19
```
sudo chmod 755 /var/log/news
ls -la /var/log/news
```

---

