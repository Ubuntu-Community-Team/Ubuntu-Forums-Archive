---
title: "How do I schedule a Python Script?"
date: 2007-03-23
forum: Desktop Environments
---

### Post by mister_p_1998 on 2007-03-23
Hi Guys,
Im trying to schedule a program start in cron, its a Python script (Democracyplayer) and just selecting the script in cron doesnt work. It runs fine from command line, just not in cron. Any Ideas?
Stev

---

### Post by pirothezero on 2007-03-23
I run sabnzbd (python nzb downloader) at startup as well as I have it start every 4 hours in case something happened where it dropped. What I did was make a bash like so:
```
#! /bin/bash
cd ~/.SABnzbd/sabnzbd
./SABnzbd.py -d -f SABnzbd.ini

```
then do 
```
chmod +x nameoffile
```
then go into cron and add this file as a task.

Maybe someone has a better way. I tried messing around with it doing stuff like ./ in the cron window and i was able to get it to close and save without errors but nothing would happen when I went to execute it. Though I imagine theres a better way.

---

