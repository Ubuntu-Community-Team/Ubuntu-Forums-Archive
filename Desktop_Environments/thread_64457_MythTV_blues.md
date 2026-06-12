---
title: "MythTV blues"
date: 2005-09-11
forum: Desktop Environments
---

### Post by dc2447 on 2005-09-11
Hi - I am trying to setup mythTv as I need to be able to record from my TV capture card - I have installed via apt however when I run mythtv or mythtv-setup I get access denied when connecting to mysql.

> davidcam@vader:~$ sudo mythtv-setup
2005-09-11 08:05:01.434 Unable to connect to database!
2005-09-11 08:05:01.435 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

couldn't open db
2005-09-11 08:05:01.435 Switching to square mode (blue)
Segmentation fault


What makes this strange is that I can login to mysql using the exact same credentials that is in mysql.txt using the cli

Anyone got any suggestions?

Are there alternative ways of recording from TV cards - other than full PVR style setups apart from using mencoder on the cli.

---

### Post by dc2447 on 2005-09-11
worked it out - need to run mythtv setup as root or it won't find the mysql.txt

---

