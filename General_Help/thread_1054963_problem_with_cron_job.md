---
title: "problem with cron job"
date: 2009-01-30
forum: General Help
---

### Post by Phicis on 2009-01-30
Hi,

I set up Twiki(4.2.4) on our Ubuntu Server 8.04 LTS. We configured the webnotify tool that sends me all the changes made on the TWiki pages.

I would like to schedule that webnotify with crontab. But that doesn't work. It displays the error:

./webnotify: line 1: 0: command not found


Content of my cron job: 

0 0 * * * cd /srv/twiki && perl -I bin tools/mailnotify -q

Can someone help me?

Thanks 

Phicis

---

### Post by dcstar on 2009-01-30
> **Phicis said:**
> Hi,

I set up Twiki(4.2.4) on our Ubuntu Server 8.04 LTS. We configured the webnotify tool that sends me all the changes made on the TWiki pages.

I would like to schedule that webnotify with crontab. But that doesn't work. It displays the error:

./webnotify: line 1: 0: command not found


Content of my cron job: 

0 0 * * * cd /srv/twiki && perl -I bin tools/mailnotify -q

Can someone help me?

Thanks 

Phicis

Don't put compound commands in a cron job, put them in a script and call the script.

There must be **hundreds** of similar posts already in the forums on this sort of thing, search them out and you should find a solution.

---

