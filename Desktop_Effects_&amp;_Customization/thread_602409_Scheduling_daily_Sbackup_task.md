---
title: "Scheduling daily Sbackup task"
date: 2007-11-04
forum: Desktop Effects &amp; Customization
---

### Post by perixx on 2007-11-04
Hello people!


I'm having problems to figure how to set up SBackup to start once a day (after PC booted, or at shutdown). 

I haven't seen any hint in the crontab docs that show a simple solution to set EVERY BOOT or EVERY SHUTDOWN (of course anacron might start deferred jobs from PC being switched off).

From what I've seen here
```
http://ubuntuforums.org/showthread.php?t=568523
```
the "at" command might be better for this job , for there are no environmental restrictions and I can specify "NOW" (for boot-up). 


BUT: where would I have to put the respective script containing the "at" command, so as Xubuntu loads it at startup?

WOULD Applications > Settings > Automatically started Applications do basically the same job?

AND: I've already set SBackup Config to start daily but I'm confused by the text and how I can specify to exclude "full" backups and do ONLY incremental ones. Currently I've set "do a full backup at least once every '0' days"; but I doesn't seem to do any backup..?

Do I have to manually write a crontab file for running a scheduled SBackup at all?


Hopefully, someone can clarify things a little...

perixx

---

### Post by perixx on 2007-11-04
*bump*

---

### Post by perixx on 2007-11-05
Can somebody figure out how to schedule a daily task for 'sbackup'?

I'm confused by the 'sbackup' entrey in /etc/cron.d, where /etc/crontab has no entry... the daily backup as set up in the 'sbackup-config'-app will not start!

What is to be done??

I'm also not sure about how to refer in the 'crontab' file to the actual 'sbackup'-program (yes, I've read all the posts for setting environments and so) - I've only recently learned, that the actual command for starting the application is 'sbackupd'. 

But if I'd use this in the crontab file, would it still start with the settings from the sbackup-configuration-app? 

Unfortunately, every documentation-site for sbackup out there only scratches this issue by mentioning, one needs 'cron' to enable scheduled tasks, but not giving any example on HOW to do it! :/

Please help!!


perixx

---

### Post by dave37 on 2007-11-13
Sbackup is a great utility, but I too am wondering if there is some way to have it do a backup, and then shutdown the system.  I'm currently using it to backup to a secure ftp and I would need the shutdown command to only complete once sbackup is finished.

---

### Post by perixx on 2007-11-14
I'll provide you with a solution, as soon as I managed to find one, dave37... currently, I'm setting up a new system for myself.

perixx

---

### Post by dave37 on 2007-11-14
Thanks, I've also found on the sourceforge site that if you're using the latest version of Sbackup, there is now a checkbox for "precisely" and "simply" for scheduled backups.  Precisely uses cron only, and the machine must be on to run at the time specified. If you choose simply, it uses anacron to start it if it was scheduled to run at some time while the pc was off.  

Note that anacron will not start the job if it was scheduled to run less than 1 day ago, and anacron also seems to vary when it will run (for example, if it was supposed to run yesterday but didn't because the pc was off, it won't start it up automatically today on boot, it will run it at some point today as specified in the delay in your /etc/anacrontab file)  Anacron seems a bit wonky, I've spent days pouring over it.  Seems in ubuntu dapper which I'm running that anacron MAY need root permission, and it only checks to see what needs to be run on start up.  I say MAY as there is some conflicting information out there.  

What is working for me is placing the following script I titled anacron.sh in my home folder:
#!/bin/sh
/usr/sbin/anacron -s

And then using the system>preferences>sessions and startup programs tab to run anacron.sh on startup.  What this apparently does is tell anacron to serialize the jobs.  I then used gnome scheduler to call anacron.sh every hour so that anacron will check hourly to see if anything should have been run by now.

As I say, the anacron info I read was conflicting, it SHOULD run without having to do everything I did, but for me it didn't seem to.

---

### Post by perixx on 2007-11-14
Thanks, dave37!

That sounds promising; of course, I'm afraid I got to wait till someone compiles the new version. That's because I didn't manage to compile a single little program on the old machine - old machine, because that's the one I had installed Sbackup onto. I doubt, that on my own computer / with Gutsy things will be much better... (granted, I got no clue on compilation so far - but just installing 'build-essential' didn't really help much.) 


perixx

---

