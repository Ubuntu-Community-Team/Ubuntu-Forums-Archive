---
title: "permissions"
date: 2009-03-19
forum: General Help
---

### Post by lex1 on 2009-03-19
I should know this by now but I have forgotton!
what must be done so that user "news" can read and write to these
file?

total 40
drw-r--r--  4 news news 4096 2009-03-19 10:35 .
drwxr-xr-x 12 root root 4096 2009-03-19 07:38 ..
-rw-r-----  1 news news  392 2009-03-17 13:40 news.crit
-rw-r-----  1 news news  392 2009-03-17 13:40 news.err
-rw-r-----  1 news news 7782 2009-03-19 10:10 news.notice
drwxrwxr-x  2 news news 4096 2008-12-14 23:51 OLD
drwxrwxr-x  2 news news 4096 2008-12-14 23:51 path
-rw-r--r--  1 root root   62 2009-03-17 13:40 rc.news


thanks

lex1;)

---

### Post by sahabcse on 2009-03-19
Hi

In Linux file default permission is 644 for directory 755.

Here the user has read and write permission.

-rw-r----- 1 news news 392 2009-03-17 13:40 news.cri

The permission of news.cri is 640, that means user has read and write, group only allow to read, others has no permission. Hope its clear for u..........

---

### Post by lex1 on 2009-03-19
thanks for your post

so if i want "news user and group to be all to read and write 
to all files in my last thread what must be done

lex1;)

---

### Post by sahabcse on 2009-03-19
Hi

Just run following command

#chmod 660 filename

---

### Post by lex1 on 2009-03-19
thanks for your post sahabcsc


#chmod 660 filename as root user but then how to create files with touch as news user if news does not have permission to acess this directory?

lex1

---

### Post by sahabcse on 2009-03-19
hi

Sudo touch filename

---

