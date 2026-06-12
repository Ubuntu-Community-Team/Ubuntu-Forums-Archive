---
title: "CRON/CRONTAB problem"
date: 2009-02-11
forum: General Help
---

### Post by Shrav on 2009-02-11
Hi all
I thought this would be an easy task but I'm finding out otherwise. all I want to do is run this:

syncevolution scheduleworld

a few times a day. I have made an executable script that does it with no problem. I can run it from command line with no issues. I have have had no luck getting adding it to a cron job as either root or user and getting it to execute. 

crontab -l shows */5 * * * * export DISPLAY=:0.0 && /home/user/bin/syncevolution_scheduleworld.sh (<-- my script) with syncevolution scheduleworld)

Tried sudo crontab with the same.

syslog shows:

Feb 11 20:40:01 user1 /USR/SBIN/CRON[9431]: (user) CMD (export DISPLAY=:0.0 && /home/user/bin/syncevolution_scheduleworld.sh)

There must be something I am missing. I have googled and read man pages for 2 days now and still can't automate this script. I have even tried */5 * * * * export DISPLAY=:0.0 && syncevolution scheduleworld and still no joy.

Can anyone point me in the right direction? Thanks in advance!

p.s. The 5 minute polling is only for testing.

---

### Post by jonlemur on 2009-02-11
I'm pretty new to cron, but it looks like you have 5 hour polling rather than five minute.  From Wikipedia:
```

# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
  *  *  *  *  *  command to be executed

```

I would try manually putting a time a minute or two after you set it to test it, rather that trying to poll every five minutes (which I haven't seen before, is that what the / does?).

---

### Post by lswb on 2009-02-11
There are often problems when trying to run an X program via cron. What is in your script? Just to narrow down where the problem is, try substituting a script that does not need do display anything. (Maybe just append a line with time and date to a file) If it runs OK at least you will know that it is a problem with X and not your crontab per se.

---

### Post by Shrav on 2009-02-11
> **lswb said:**
> There are often problems when trying to run an X program via cron. What is in your script? Just to narrow down where the problem is, try substituting a script that does not need do display anything. (Maybe just append a line with time and date to a file) If it runs OK at least you will know that it is a problem with X and not your crontab per se.

Hi
The script is only this:

syncevolution scheduleworld

As you can see it isn't fancy. It does not need to display anything. Running in the background would actually be preferred. All it does is sync evolution with scheduleworld so I don't really need to see it. I just know that if I manually type it into a terminal or execute the script any changes get synced. If I let cron do its job they don't. Suggestions?

---

### Post by lswb on 2009-02-12
Try including the complete path to the syncevolution command in your script (and to scheduleworld if it is the name of a file)

If the command does not display anything you can probably skip setting the DISPLAY variable.

---

