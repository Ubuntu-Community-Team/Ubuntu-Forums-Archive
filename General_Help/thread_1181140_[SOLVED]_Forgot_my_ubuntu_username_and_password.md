---
title: "[SOLVED] Forgot my ubuntu username and password"
date: 2009-06-07
forum: General Help
---

### Post by amitg on 2009-06-07
[SIZE=3]I am new to ubuntu and installed the software on my desktop. For some time I did not use it and when I tried to log in again I discovered that I forgot my username and password. Any suggestions?[/SIZE]

---

### Post by jbruced on 2009-06-07
Google,

It's against policy to show how to bypass passwords here.

---

### Post by michy99 on 2009-06-07
Not against policy:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by shredder12 on 2009-06-07
when the grub screen loads boot in ubuntu's recovery mode..
by default u will get a command prompt with root privilages..
do
```
ls /home
```
this will list you the name of users.
find ur's..
then run this command

```
passwd you_username
```
and change the password for the user name
then restart with you username and changed passwd

---

### Post by amitg on 2009-06-07
Thanks a lot. I followed the instructions, found my username and reset my password. Then I could log in again! ):P

---

### Post by shredder12 on 2009-06-07
always ready to help.. :)

---

