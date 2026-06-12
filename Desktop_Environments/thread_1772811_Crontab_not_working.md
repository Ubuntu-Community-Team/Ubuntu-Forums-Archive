---
title: "Crontab not working"
date: 2011-06-01
forum: Desktop Environments
---

### Post by MocniMis on 2011-06-01
Hi!
Well I made a typo and deleted my root crontab where I had all my cronjobs.
Now, my .sh scripts are running fine when I run them in terminal but cron just ignores them or something :(

Cron is running:

root@hp-bika:/home/sergej# sudo status cron
cron start/running, process 1008

And here is how it looks now:

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command

* * * * * root /home/sergej/Documents/ShellScripts/BugReport.sh >> /home/sergej/Desktop/err.log 2>&1

Any help would be appreciated.:)

---

### Post by tapi0n on 2011-06-01
> 
* * * * * root /home/sergej/Documents/ShellScripts/BugReport.sh >> /home/sergej/Desktop/err.log 2>&1you don't have any time specified as to when to run the command?

why do you put *root *in front of  */home/sergej/Documents/ShellScripts/BugReport.sh *? When you do a local run of your script you do *sh /path/to/script.sh *right? So why not do it in crontab like that too, I had an issue with crontab not running either some time ago and that was my problem too.

---

### Post by MocniMis on 2011-06-01
Well, i've been trying everything so root got there as root user.
I'll remove it now and try to > */1 * * * * command

---

### Post by MocniMis on 2011-06-01
Nope, that didn't help.

---

### Post by tapi0n on 2011-06-01
Is it possible there is a problem with the paths in your script? When you want a cronjob to run a script you need to use full path names in the script.

---

### Post by MocniMis on 2011-06-01
Well I think scripts are fine because they were all running two days ago (before I "fixed" my crontab).
I think I'm an idiot cause I did not made any backups for the crontab :(

---

### Post by tapi0n on 2011-06-01
So they were running as cronjobs before without any trouble, why not make a new crontab for root then? Instead of a system-wide crontab (which is with different permissions iirc?).

Sorry if I'm not of much assistance, haven't been using this stuff for very long myself, trying to help you out as much as I can ;).

---

### Post by MocniMis on 2011-06-01
No problem, like i've said ANY help would be appreciated.
Well yes scripts were running in a system wide crontab but I made a typo "crontab" instead of "crontab -e" and crontab was empty when I tried "crontab-e" later.

I'm trying now to "mkdir" and nothing is happening.

---

### Post by sgardne on 2011-06-01
My crontab has also started exhibiting strange behavior. It would appear from the logs, that it has only run on the 31st of May during the last 10 days, however some of these jobs are set to run every 5 minutes.

```
# crontab -l
# m h  dom mon dow   command
*/5 * * * * /usr/bin/perl /usr/local/bin/perl/managed_arp_data.pl >> /var/log/arpdb.log
*/5 * * * * /usr/bin/perl /usr/local/bin/perl/infoblox_fixed_sync.pl >> /var/log/crossref.log
00 23 * * * /usr/bin/perl /usr/local/bin/perl/infoblox_host_sync.pl >> /var/log/host_sync.log
0 * * * * /usr/bin/perl /usr/local/bin/perl/infoblox_excl_sync.pl >> /var/log/excl_sync.log
```

I think I've set cron to run at log level 1, but I can't seem to find where it dumps those logs. Anyone know where crontab is logging to?

---

