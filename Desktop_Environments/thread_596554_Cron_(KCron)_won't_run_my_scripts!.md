---
title: "Cron (KCron) won't run my scripts!"
date: 2007-10-29
forum: Desktop Environments
---

### Post by sebald on 2007-10-29
Since upgrading my system from 6.06 to 7.04, the audio capture scripts I wrote won't run from cron, where they worked fine before!! 

I'm using scripts that invoke mplayer to dump streams to a file with date/time stamps, and use kcron instead of writing cron jobs directly. All the scripts run fine when invoked manually. They're placed in /usr/local/bin, and run from a straight command, without the ./ prefix . Have tried changing users from root to myself, etc, no luck. The syslog shows that cron invoked the command at the right time, but nothing happened. 

:confused:

---

### Post by asipi on 2007-10-30
copy here the result of command **crontab -l** of all users you want to run the script for info
write the whole path of the script in the crontab entry (just for sure)
modify your scripts, try to redirect the STDERR to a file e.g. error.log to check what errors happened
take consider that cron using different environmental variables that your user have when starting the crontab entries, so even the PATH could be different

---

### Post by sebald on 2007-10-30
After experimenting and reading a bit, it looks like the verbosity of MPlayer's output was the problem - added an option to the mplayer command line to suppress all message output and it ran fine! Don't know why it became a problem only after my upgrade, but that is the answer for now. 

Example script: wxxi-whav-local.sh:
------
#!/bin/bash
#live capture of WXXI, Rochester - activate with cron or kcron
OF=/home/john/server/www/lorenz-root/with-heart-and-voice/$(date +%y%m%d%k%M)-whav.mp3
DELAY=7200 # variable for number of seconds of program length
mplayer [http://66.195.169.113:80/fm-hi](http://66.195.169.113:80/fm-hi) -msglevel all=-1 -dumpstream -dumpfile $OF
sleep $DELAY
kill %-
-----
MPlayer, cron, and some scripts like this are just great for automated capture of program streams.

BTW I'm mastering crontab editing from the command line - not that hard, so will slowly dispense with the GUI aids like kcron...

The music now rocks on :guitar: - on demand for later listening!

---

