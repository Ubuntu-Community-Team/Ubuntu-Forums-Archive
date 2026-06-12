---
title: "How Do I Setup Cron Job?"
date: 2006-02-18
forum: Desktop Environments
---

### Post by emut on 2006-02-18
I am running a CRM package that requires a cron tab to process some scheduled jobs but I have no idea how to set one up!  Have read through some guides but am still not sure.  If possible I need it to run every minute.

The info from the program is that I have to set up a cron job with the line,

Add this line to your crontab:
*    *    *    *    *     cd /opt/lampp/htdocs; php -f cron.php > /dev/null 2>&1 

Where do I add this line?  Is it in /etc/cron.hourly?

Any help would be much appreciated.

---

### Post by kabus on 2006-02-18
Enter "crontab -e" at a terminal to add a cronjob for your user (or "sudo crontab -e if the job needs to run as root). Then paste that line you have into the editor that comes up and change it to : 

*/1 * * * * cd /opt/lampp/htdocs; php -f cron.php > /dev/null 2>&1

to run it every minute.

There's also a guide at the wiki :

[https://wiki.ubuntu.com/CronHowto](https://wiki.ubuntu.com/CronHowto)

---

### Post by heimo on 2006-02-18
I'd guess that you need to add that to the crontab of the user that runs the application. I'd try:
```
EDITOR=pico sudo crontab -u www-data -e
```

Where www-data is the correct user to run these batch jobs, and pico is your favourite text editor. (defaults to vim, I guess)

---

### Post by emut on 2006-03-13
Thanks for your help, now sorted \\:D/

---

