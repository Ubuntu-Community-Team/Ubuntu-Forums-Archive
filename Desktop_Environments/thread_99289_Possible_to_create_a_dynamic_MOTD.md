---
title: "Possible to create a dynamic MOTD?"
date: 2005-12-05
forum: Desktop Environments
---

### Post by OneSeventeen on 2005-12-05
I was thinking it would be cool to have the /etc/motd file be dynamic, so each time it is displayed, it shows a different message.  Is this possible?

I'm mainly only doing this for SSH connections, I'd like to have a different quote appear each time someone ssh's in to work on it.  I can easily write a shell script that would randomly choose a quote from an array, but don't most scripts just echo /etc/motd ?  would that execute it?  or is it impossible to create a dynamic MOTD?

(I know I could probably write a script that physically changes the motd each time someone logs in, but that's a little too out of the way for somthing this pointless.)

---

### Post by earobinson on 2005-12-05
if you man motd I think it will tell u the file that motd is read out of, it should be simple to write a simple sh script or program to put in your cron jobs to replace it every dat or even hour.

Second idea is write a program and just replace /etc/motd with it. (back up the old motd. then instead of the motd program being called it would be yoru program that gets called.

But i dont know of any programs that do this. so sorry think you gota do some programing. If you do write a program post it.

---

### Post by xmastree on 2005-12-05
well, I'm not sure about motd, but have you looked into **fortune**?

---

### Post by astoltz on 2005-12-05
Found [this]("http://lists.debian.org/debian-user/1997/06/msg01397.html") on the debian list which might be helpful.  But to get the file to change EVERY time it is displayed, i'm afraid you're gonna have to do some fancy scripting.  I don't think it's as simple as just replacing /etc/motd with a program.  

You could "fake" it by running a cron job that changes the contents of /etc/motd every x minutes.

---

### Post by PokerFacePenguin on 2005-12-06
[QUOTE=xmastree]well, I'm not sure about motd, but have you looked into **fortune**?[/QUOTE]
Fortune was what came to my mind too...


fortune > motd.txt
  (or whatever the motd filename is) in a cronjob should do the trick for rotating the motd file.  

hourly should do the trick since the users probably aren't logging in more than once in an hour

---

