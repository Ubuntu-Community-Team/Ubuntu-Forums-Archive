---
title: "cron not running"
date: 2009-03-08
forum: General Help
---

### Post by kpm on 2009-03-08
I have a bare bones server that I realized didn't have cron installed, so I used apt to install.  Logged in as root, I ran 'crontab -e' and set a cron job up for a drupal site.  that job seems to be running.  However, when I run the 'locate' command, I am greeted with the warning message:
"locate: warning: database `/var/cache/locate/locatedb' is more than 8 days old (actual age is 13.8 days)"
Since that update resides in the cron.daily, I am led to beleive that none of the cron.daily scripts are running.
Can anyone tell me how I can get these system maintenance scripts to run??
Thanks

---

