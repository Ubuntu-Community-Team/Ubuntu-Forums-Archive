---
title: "please help - cron job wont run!"
date: 2006-06-25
forum: Desktop Environments
---

### Post by guy_uk on 2006-06-25
Hi folks

My hoary server is causing me stress :(

I have a dvdrw drive, and i want it to backup my home folder to dvd daily.

this is the command i run:

growisofs -v -Z /dev/hdc -disable-deep-relocation -allow-leading-dots -U -no-rr -allow-multidot -no-iso-translate -allow-lowercase /home/

This is in my crontab for root (i have however tried as a user). If i cut and paste the command straight out of the crontab into a root or user terminal it runs fine and copies /home (3 gig) to the dvdrw with no issues.
But when the specified cron job run time is reached, the command doesn't run, instead i can see a session open in my syslog and close either immediately or a couple of seconds later.

the crontab has another copy command and this runs fine??

my crontab is as follows:-
#cron jobs
08 22 * * * cp -R /home/ /MIRROR/home/
23 13 * * * growisofs -v -Z /dev/hdc -disable-deep-relocation -allow-leading-dots -U -no-rr -allow-multidot -no-iso-translate -allow-lowercase /home/

Please help! :( what am i doing wrong??

Thanks

Guy

---

