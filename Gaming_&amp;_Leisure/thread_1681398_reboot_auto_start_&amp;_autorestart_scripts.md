---
title: "reboot auto start &amp; autorestart scripts"
date: 2011-02-04
forum: Gaming &amp; Leisure
---

### Post by Fakar on 2011-02-04
Hi,

i am runing dedicated with ubuntu 10.10

Now what i would like to have is auto restarting servers.
for example, i have made .sh files for each user that runs server

usaly when i reboot server i login as user1 and execute /home/user1/start.sh
that starts server and 1 mod together. I have 5 users (5 servers)
now that i wouldnt have to login in each account and do that all the time, and also wait till 2-4 am to restart server (since players are on all the time) i would like something like autorestart or cron or dunno. If someone could explain me.

so i would like this

if i'm working with server and i reboot it by myself i would like that on system load up all server startup up
user 1 executes /home/user1/start.sh
user 2 executes /home/user2/start.sh
user 3 executes /home/user3/start.sh
user 4 executes /home/user4/start.sh
user 5 executes /home/user5/start.sh

and at 5 am i would like auto restart (not whole server only that uses stop.sh and then start.sh)

if i do that manualy i login with user1, type screen -r and say server will restart (if there are players on) and then click ctrl + c to stop it and use start.sh to start it.

so i would like to autorestart at 5am like this example
user1 -> screen -r -> type in console say Server will auto-restart in 30 seconds -> Server will auto-restart in 20 second -> Server will auto-restart in 10 seconds> Server will auto-restart in 5 seconds -> waits 5 seconds and uses /home/user1/stop.sh wait 5 sec executes /home/user1/start.sh

and for next for users same

Point to going into screen and say server will... is because also american users might be online at that time so they know what is happening.

hope i have explained well also other way guid would be nice if system instead of stop.sh and start.sh would only use reboot (reboots whole server) and ofc before it would say. So in case if i would use that a weekly or monthly

Regards
and thanks forward for some guids for newbies.

---

