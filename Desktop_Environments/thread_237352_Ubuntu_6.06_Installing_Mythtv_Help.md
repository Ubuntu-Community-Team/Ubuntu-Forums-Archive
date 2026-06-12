---
title: "Ubuntu 6.06 Installing Mythtv Help"
date: 2006-08-16
forum: Desktop Environments
---

### Post by Jmerlos on 2006-08-16
Does anyone know what I'm doing wrong. I'm trying to open phpmyadmin and instead of opening it's tring to look for a program to open with or save off. 
Also when running mythtvbackend I get this error

mythbackend
2006-08-16 01:56:40.568 Using runtime prefix = /usr
2006-08-16 01:56:40.584 New DB connection, total: 1
2006-08-16 01:56:40.591 Connected to database 'mythconverg' at host: localhost
2006-08-16 01:56:40.596 Current Schema Version: 1120
2006-08-16 01:56:40.597 Newest Schema Version : 1123
2006-08-16 01:56:40.598 New DB connection, total: 2
2006-08-16 01:56:40.599 Connected to database 'mythconverg' at host: localhost
2006-08-16 01:56:40.600 Setting Lock for Database Schema upgrade. If you see a long pause here it means the Schema is already locked and is being upgraded by another Myth process.
2006-08-16 01:56:40.601 New DB connection, total: 3
2006-08-16 01:56:40.601 Connected to database 'mythconverg' at host: localhost
2006-08-16 01:56:40.602 Upgrading to schema version 1121
2006-08-16 01:56:40.603 DB Error (Performing database upgrade):
Query was: UPDATE keybindings SET action = 'ADJUSTSTRETCH'        WHERE action = 'TOGGLESTRETCH';
Error was: Driver error was [2/1062]:
QMYSQL3: Unable to execute query
Database error was:
Duplicate entry 'TV Playback-ADJUSTSTRETCH-VAIO' for key 1

new version: 1121
2006-08-16 01:56:40.604 Database Schema upgrade FAILED, unlocking.
2006-08-16 01:56:40.604 Couldn't upgrade database to new schema

---

### Post by DoctorMO on 2006-08-16
If you can remove MythTV and all it's databases and try reinstalling the latest version. this looks like a problem with a new version updating the database.

---

### Post by Jmerlos on 2006-08-17
Thank you for your reply, I will give it a shot

---

