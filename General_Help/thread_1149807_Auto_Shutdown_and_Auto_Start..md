---
title: "Auto Shutdown and Auto Start."
date: 2009-05-05
forum: General Help
---

### Post by ashmew2 on 2009-05-05
Hi everyone  ,
I was wondering if there is  a way to auto start my system at say 8:00 every morning.
We have power cuts here from 7 AM to 8 AM. I usually put an auto shutdown for 6:30 AM but i usually sleep till 11~12. I use bittorrent for seeding/leeching etc , and i wanted to know if i could get my system to Auto start and automatically run a bittorrent client (maybe rtorrent) without logging in and automatically starting an incomplete file download.

Is it possible ?

Thanks! :D

---

### Post by kpkeerthi on 2009-05-05
To autostart: Check in your BIOS. There should be an option to auto start the computer.
To autoshutdown: You can put **/sbin/shutdown -h now** in your sudo's [crontab]("https://help.ubuntu.com/community/CronHowto")

---

### Post by ashmew2 on 2009-05-19
Thanks for the reply..I found an option in the BIOS :D

Thread Solved :D

---

