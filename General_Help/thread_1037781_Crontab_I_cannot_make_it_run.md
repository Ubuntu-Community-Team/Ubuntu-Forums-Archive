---
title: "Crontab: I cannot make it run"
date: 2009-01-12
forum: General Help
---

### Post by septekin on 2009-01-12
Can someone please tell me what I'm missing to start a cron job.

When I enter "nautilus" in the Terminal, the File Browser starts. If I want it to start at, say, 09:00, I enter in the Terminal "crontab -e" and edit it to contain "00 09 * * * nautilus. I now check it:

```
hp: ~\$ crontab -l
# m h  dom mon dow   command
00 09 * * * nautilus
hp: ~\$ 
```

When 09:00 comes and passes nothing happens.

I'm running Hardy on an HP Pavilion zv6245. I've tried the same procedure on a Sony Vaio VGN-FZ21M, running Gutsy: again nothing.

My user name is included in /etc/cron.allow. /etc/cron.deny does not exist.

My guide is the -excellent- article:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

I've tried icluding the full path to the command, no change.
Yes, I did check the system date and time!
By the way, I want to use crontab to run my daily backup script so that I won't have to do it manually first thing every morning.

Where on earth am I failing?

Thanks in advance,

teoman

---

### Post by bluefrog on 2009-01-12
0 9 * * * export DISPLAY=:0.0 && /usr/bin/nautilus

if your display is :0.0

check with env | grep DISPLAY

for the script, no need to export the display as it will be run in the background.

---

### Post by ajgreeny on 2009-01-12
Yes **cron** will only run GUI applications if you tell it to use the appropriate display with the **export DISPLAY=:0.0 && **at the front of your command.  If you have more than one display it may be another number.

---

### Post by septekin on 2009-01-12
Thank you bluefrog. The addition of export.. did show the nautilus but I still cannot run my script. My relevant entry is similar to: "50 12 * * * /home/user/script_xxx".
When the time comes there is hard disk activity but no result. The script is executable but I also tried "50 12 * * * /home/user/./script_xxx" and escape characters before the . and the / : so far so bad. Any further help you can give?

---

### Post by septekin on 2009-01-12
..and thank you ajgreeny. Maybe you would like to have a look at my #4!

---

### Post by ajgreeny on 2009-01-12
No problem.  I presume your script runs OK if you use it normally in terminal or by double clicking.  Also can I ask if you have used or tried gnome-schedule to run the script as well as cron direct.  Perhaps it might help to see the script you are running as this may also give a clue, depending on what the script uses to run the backup you may still need the DISPLAY notation.

---

### Post by septekin on 2009-01-12
ajgreeny, if you have the time and patience I believe you can solve my problem: including the export.. bit did run my script, but instead of doing a backup it jumped to the end and displayed the contents of the last backup. I've been using this script (or its predecessors) regularly for over a year via a key combination set in Configuration Editor.

I'm adding a copy of my script (is it really necessary to be so paranoid as to remove the paths and file names?) as I believe a little modification is indicated.

```
#!/bin/sh
# ts: 081130

#  Creates a directory named yymmdd in WHATEVER and
## backs up /home/USER and others, without changing their timestamps;
## hidden files are included.

xmessage "Starting backup_hp" -timeout 8

DATA=/media/XX
BACK=/media/XX	
yymmdd=`date +%y%m%d`
mkdir $XX/$yymmdd

rm -fr /XX/.evolution/cache/tmp
rm -fr /XX/.mozilla/firefox/XX.default/Cache/*
rm -fr /XX/.thumbnails/*

cp -fprv /home/USER $BACK/$yymmdd

cp -fprv $XX $BACK/$yymmdd
cp -fprv $XX $BACK/$yymmdd
cp -fprv $XX $BACK/$yymmdd
cp -fprv $XX $BACK/$yymmdd

nautilus $BACK/$yymmdd

exit
```

Thanks once again.

teoman

---

### Post by septekin on 2009-01-13
I am marking this thread as SOLVED and start a new thread: not seeing the GUI applications misled me to believe that cron was not running. It is running but the script is not executed properly.

My thanks again to bluefrog and ajgreeny for my education.

---

