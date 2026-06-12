---
title: "Can I log in as the mysql user?"
date: 2009-03-03
forum: General Help
---

### Post by mylar on 2009-03-03
version: 8.10 server
I have installed mysql and I can connect to it and use it just fine. I am reading a book about mysql (Mysql by Paul DuBois 2005) and it says that you should run myisamcheck as the mysql user. Also some regular maintenance should be scheduled in the mysql user's crontab file. Sadly I can't seem to log in as the mysql user. So my questions are: can I login as mysql? and if so how? or should I get a different book? if so which one?

Thanks.

---

### Post by Ubunbun on 2009-03-13
Are you able to log in as admin? *mysql -u root -p* 

When you enter *mysql* does it take you right into mysql with out a pass?

---

### Post by mylar on 2009-03-17
What I originally meant is can one log into the linux machine as the user mysql - not log into the mysql server. It seems you can do most stuff using sudo but it's a pain since I have to keep changing file permissions back to mysql.

---

