---
title: "Game Server Monitoring Software"
date: 2009-05-11
forum: Gaming &amp; Leisure
---

### Post by zhelev81 on 2009-05-11
Is there out there any program that I can use for Monitoring my servers and sending rcon commands to them to check they are up and running ?And if not,action to be taken.

For example I have counter strike source servers and run them in background screens but sometimes the servers do errors and don't restart themlelfs auotmaticaly.In this case The screen freezes and if you  don't kill it u cannot do anything else.

My question is... Is it possible a small program to be created to do the forllowing :

Sending "rcon status" every 10 sec and if the server do not reply on it to kill the screen and Strart the server again.

Or maybe there is already some program to suite my needs ?

I'll appreceate your help .Tnx

---

### Post by Triptol on 2009-05-11
You might want to take a look at nagios ([http://www.nagios.org/](http://www.nagios.org/)). It might be a bit more than you want though. There are other cool projects out there. If you Google for "network monitoring linux", or something, you will find them.

---

### Post by glotz on 2009-05-11
Also check out XQF and Qstat.

---

### Post by W Moore on 2012-07-16
In case you are still looking for a game server monitoring tool, check out Circonus.
[www.circonus.com]("http://www.circonus.com").  Inexpensive, all inclusive, totally supported, easy to use...

---

### Post by boast on 2012-07-17
I use [monit](http://mmonit.com/monit/) to make sure my mail and http server always start up if they crash. Maybe it can work for game servers too?

---

### Post by vectorzx on 2013-07-14
I don't know whether it's still valid to reply this thread or not because the OP asked this question was in 2009. But if you're still looking on how to monitor your site, you can take a look on [socketone.com](http://socketone.com). You can add various Steam games through the site.

Thanks.

---

