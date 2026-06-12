---
title: "Stop cron sending email"
date: 2009-03-13
forum: General Help
---

### Post by dannyboy1121 on 2009-03-13
Hi Folks,

I'm running a script every 5 minutes from crontab to update some minor report.

The issue I have is that cron is sending out emails every time the job is run ..

My crontab entry is:

*/5 * * * * /scripts/reports.sh /dev/null 2>&1

I thought that /dev/null 2 >&1 tagged at the end would kill off the mail but I'm still getting them

Any ideas?

---

### Post by lutherhex on 2009-03-13
If you don't want it to email you, then why not remove the send email code from your /scripts/reports.sh?

If you do want it to email you, then create a new cron job at long intervals to then email you what you need.

JES

---

### Post by dannyboy1121 on 2009-03-13
No sendmail code in the script .. just a feature of crontab

I've found the error - syntax

Was:
*/5 * * * * /scripts/reports.sh /dev/null 2>&1

Should have been:
*/5 * * * * /scripts/reports.sh **>**/dev/null 2>&1


There .. I'm not getting spammed by the mail server now :D

---

### Post by heindsight on 2009-03-13
If you want to completely stop cron from sending you email, without having to redirect the output of every command in your crontab to /dev/null, then you can change the value of the MAILTO variable in your crontab file.

just put a line like:
```
MAILTO=""
```
at the top of your crontab.

---

