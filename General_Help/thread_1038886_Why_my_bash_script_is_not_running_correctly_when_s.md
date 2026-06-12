---
title: "Why my bash script is not running correctly when started by crontab?"
date: 2009-01-14
forum: General Help
---

### Post by septekin on 2009-01-14
Can someone please tell me why?

The following script runs as expected when started in Terminal; when it is started by crontab it performs a partial backup. Here is the script:


```
#!/bin/sh
# ts: 081130

#  Creates a directory named yymmdd in LaCie320/pavilion/BACKUP and
## backs up /home/teoman and others, without changing their timestamps;
## hidden files are included.

xmessage "Starting backup_hp" -timeout 8

DATA=/media/hda8
BACK=/media/lacie320/BACKUP	
yymmdd=`date +%y%m%d`
mkdir $BACK/$yymmdd

rm -fr /home/teoman/.evolution/cache/tmp
rm -fr /home/teoman/.mozilla/firefox/*.default/Cache/*
rm -fr /home/teoman/.thumbnails/*

cp -fprv /home/teoman $BACK/$yymmdd

cp -fprv $DATA/Correspondence $BACK/$yymmdd
cp -fprv $DATA/Documents $BACK/$yymmdd
cp -fprv $DATA/FreeM $BACK/$yymmdd
cp -fprv $DATA/States $BACK/$yymmdd

nautilus $BACK/$yymmdd

exit

```


Here are the contents of todays backup, performed manually (I've changed the folder name):

```
hp: /media/lacie320/BACKUP/_090114\€ lsl
total 20K
drwxrwx---  5 teoman teoman 4,0K 2008-09-20 09:49 Correspondence
drwxrwx---  4 teoman teoman 4,0K 2008-08-16 17:12 Documents
drwxrwx---  7 teoman teoman 4,0K 2008-05-21 22:31 FreeM
drwxrwx--- 10 teoman teoman 4,0K 2008-11-19 08:32 States
drwx------ 56 teoman teoman 4,0K 2009-01-14 04:58 teoman

```
The backup took six and a half minutes.

Here is the crontab entry:

```
hp: ~\€ crontab -l
# m h  dom mon dow   command
52 06 * * *  export DISPLAY=:0.0 && /home/teoman/script_bu_hp
hp: ~\€ 

```

Here are the contents of the resulting backup (which lasted less than a minute):

```
hp: /media/lacie320/BACKUP/090114\€ lsl
total 20K
drwx------ 3 teoman teoman 4,0K 2009-01-14 06:52 Correspondence
drwx------ 3 teoman teoman 4,0K 2009-01-14 06:52 Documents
drwx------ 3 teoman teoman 4,0K 2009-01-14 06:52 FreeM
drwx------ 5 teoman teoman 4,0K 2009-01-14 06:52 States
drwx------ 4 teoman teoman 4,0K 2009-01-14 06:52 teoman
hp: /media/lacie320/BACKUP/090114\€ 

```

My home folder contains 120 items as listed in Nautilus, the backup by crontab lists only four. I also note that there are discrepancies in permissions and time stamps.

What is going on?

teoman

---

### Post by lykwydchykyn on 2009-01-14
Try redirecting the output of the script into a log file, that may help diagnose. I don't know why cp wouldn't work, but I tend to prefer rsync for this kind off situation.  rsync -av would do what you want.

---

### Post by Jeff Johnston on 2009-01-14
Make sure you understand who the program runs as with cron versus manually.

At work I recently ran into this and found out that the cron job runs as a different user. By running as a different user the environment is totally different. One thing I ended up doing was give an absolute path to programs that it used. I'm not saying that that is your solution, but that was what fixed my problem.

---

### Post by septekin on 2009-01-14
I use rsync to keep my two laptop contents in sync. Here I want just a basic copy function, hence the cp command.

Here is something crazy: I tried the following entry in crontab:

58 08 * * *  export DISPLAY=:0.0 && /home/teoman/script_bu_hp > log.TXT

Lo and behold, I have a complete, correct backup and a huge log.TXT file.

I then run the following:

58 08 * * *  export DISPLAY=:0.0 && /home/teoman/script_bu_hp 2> error.TXT

The script run for a few seconds, made a partial backup. error.TXT is absolutely empty. ???

---

### Post by hyper_ch on 2009-01-14
I use this in cron to mail myself stuff:

```

0 1 * * * /path/to/script.sh 2>&1 | mail -s "SUBJECT" user

```
Just use "user" if you want to sent it to a given "user" on that system or

```

0 1 * * * /path/to/script.sh 2>&1 | mail -s "SUBJECT" user@email.com

```
Or this to send a real email.

---

### Post by septekin on 2009-01-14
Thanks for your response hyper_ch but I don't think we're in tune: I do not need to send any info to "user"; I would like to know why a script that runs perfectly in Terminal does silly things when run by cron.

(By the way, mail does not appear to be included in Hardy Heron; mailx or mailutils were suggested when I tried it. However, as I said, I have no use for them).

My latest situation: the given script runs correctly as long as I include a redirect for stdout in crontab:

```
00 04 * * * export DISPLAY=:0.0 && /home/teoman/script_bu_hp > null
```
I don't suppose I'll ever find out why.

Cheers.

---

### Post by hyper_ch on 2009-01-14
well, you might want to send you output of what's going on - especially while it's not working ;)

---

### Post by dagnabit dang doohickey on 2009-01-14
Sounds like your script is choking on verbosity.

---

### Post by septekin on 2009-01-15
May well be! However, it certainly is swallowing the lot -and seemingly enjoying- when running in good old Terminal.

---

### Post by septekin on 2009-01-15
Thank you hyper_ch, I redirected the error output to a .txt file which remained empty. When I redirected stdout to a .txt file it filled with the details of all the backed-up files. My problem disappears when I add a redirect to the crontab; this morning it made the expected backup fully: I will have to live with it not knowing why.

In the meanwhile, whatever happened to the option Mark as Solved, wasn't it under Thread Tools?

---

### Post by dagnabit dang doohickey on 2009-01-15
If you're not interested in generating a log for the backup process, remove the verbose option from the cp commands. Else, leave the verbosity as is and continue using stdout redirection.

You may also want to consider using bash instead of dash. sh has been a symlink to dash for some time now. I believe the last version of Ubuntu in which sh pointed to bash is Dapper.

---

### Post by septekin on 2009-01-15
Yes dagnabit, the verbosity bit was a leftover when I was verifying the script long time ago. Once removed the cronjob runs smoothly and correctly.

Now, how can I mark this lot SOLVED?

---

