---
title: "Every half an hour backup script"
date: 2009-03-05
forum: General Help
---

### Post by josko88 on 2009-03-05
Hello, I got my Ubuntu 8.10 on my PC today, a few hours ago and I started to modify bot source to run on Linux machines and I did it so now I want to put it on the RAM disk (/dev/shm) as I dont want the bot (its for gaming) to run on my HD as it has a nice amount of information in the database! 

It looks like this (would look):
 - 2 bots in different folders would run in /dev/shm (one is /dev/shm/ghost and the other one is /dev/shm/chat)
 - every half an hour the script would backup the /dev/shm/ghost/logs and /dev/shm/chat/logs to /home/hax/ghost/logs and /home/hax/chat/logs respectively
 - logs are named by dates and are .txt files, so a log from one day (the PC is 24/7 up) would replace itself 48 times before its complete

Is this possible and would anyone be so nice and make it? I couldnt find nothing similar using Google and search here on the forum.

---

### Post by rbmorse on 2009-03-05
sbackup will do that. It's in repository.

---

