---
title: "(More or less) Advanced Cron"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Roque on 2006-09-02
Hi,
I wrote a cron job that runs a script every 2 hours:
00 */2 * * * myScript.sh

The problem is that cron starts counting time at system startup. If want the job to run
at 00, 02, 04, 08, ..., 18, 20, 22

I can do this with
00 00,02,04,08,{list goes on},18,20,22 * * * myScript.sh

But this assumes that I want the sequence to start at 00. If instead I need it to start whenever I update the crontab (let's say, at 05:23) and subsequently (07:23, 09:23,...) 

How could I do this? Thanks in advance

---

