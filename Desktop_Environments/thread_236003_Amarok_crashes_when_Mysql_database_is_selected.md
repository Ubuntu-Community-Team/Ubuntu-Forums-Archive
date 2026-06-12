---
title: "Amarok crashes when Mysql database is selected"
date: 2006-08-14
forum: Desktop Environments
---

### Post by vavoem on 2006-08-14
Hi

I have 2 computers one of them contains a vast amount of mp3's 
I run Amarok with an Mysql database to manage them.

My other computer an old laptop (compaq armada e500) is located elsewhere. 
Because of speed i decided to connect to my mp3 collection using the database wich resides on my maincomputer.

I tested with the mysql client with the following commands and it connected without problems.

Mysql -h server -u laptop -p
connect amarok
select * from artist;

I've also made sure i have write access on the database by using an update query.
So there is no problem with that.

I've setup a samba share on the main computer and mounted it on my laptop on the same location as on the maincomputer.

I can read and write there without problems.


No here's the trouble when i select a mysql database in, configure amarok=>collection, amarok crashes when i click apply or ok. I cannot start amarok anylonger. When i remove ~/.kde/share/config/amarokrc it starts without problems.

When i build the collection on the laptop itself using the built in database i have no problems.
Thing is the laptop is so damn slow i just want to use the database on the main computer. I run amarok from the standard repo's.
;)  Thanks

---

### Post by vavoem on 2006-08-14
Can someone help me?

---

