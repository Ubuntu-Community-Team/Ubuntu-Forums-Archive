---
title: "Getting Su'ed from Shell"
date: 2006-04-16
forum: Desktop Environments
---

### Post by index_0@ya.com on 2006-04-16
Hi thr, 
       I wrote a shell script to connect to my adsl-connection , but every time it has to run , it requests for root password, Is thr anyway pass password as argument   to su command , so i can start my shortcuts  easily ? 

Cheers, 
Thx in advance ,

---

### Post by IYY on 2006-04-16
You can do it quite easily using a pipe, but it's a -very- unsafe thing to do.

---

### Post by dermotti on 2006-04-16
[http://www.ubuntuforums.org/archive/index.php/t-75610.html](http://www.ubuntuforums.org/archive/index.php/t-75610.html)


make something out of there could give you ideas

---

### Post by aysiu on 2006-04-16
Edit the /etc/sudoers file and add a line that says ```
*username* ALL = NOPASSWD: */path/to/command/actual-command*
```

---

### Post by index_0@ya.com on 2006-04-16
Hi thr, 
 Thx for ur replies, ...
 I tried one by one , the first one was the wiki thread , which lead to a solution which asks for a password , which i didnt look for , 
 the secoond one offered me to edit suores files , which i messed up and finally got restored back ( think it's a dangerous to edit tht file !! ) 

ok .. i think the piping option seems more viable  , and it's because  i am the root itself, i dont mind writing a script to launch as root , 

Let me make u clear , wht i ( or anyone else) wanted to do , is write a script to launch it in a arbitary time, so i dont need to be present to enter the password 
,


so how do i pipe it to a sudo command ? or is thr any other ways to do it  .... 
pls help 

cheers,

---

