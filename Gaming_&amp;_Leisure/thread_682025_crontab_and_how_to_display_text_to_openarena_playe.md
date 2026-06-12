---
title: "crontab and how to display text to openarena players in intervals during game."
date: 2008-01-29
forum: Gaming &amp; Leisure
---

### Post by drarem on 2008-01-29
**server_file.sh (ran from terminal):**
cd $HOME/Games/openarena-0.7.0
crontab motd.txt
./ioq3ded.i386 +set dedicated 2 +set net_port 27960 +exec test_server.cfg

**motd.txt:**
* * * * * export DISPLAY=:0 && rcon <passwd> say "Doh!"

**also tried:**
* * * * * rcon <passwd> say "Doh!"

**and**
*/1 * * * * rcon <passwd> say "Doh!"



I do a crontab -l  and it shows the cron job, and cron is running.

Is there something I'm missing?  Note:  crontab doesn't require a user if running non-root.

---

