---
title: "Cron &amp; Anacron"
date: 2006-09-14
forum: Desktop Environments
---

### Post by subzero79 on 2006-09-14
I have some issues understanding cron and anacron

For what i've search & understand Cron will run a script(or command) at specific moment (time,date,recurrence or frecuency)...that's ok. Cron the is best for machines running 24/7 (servers for example).

On the other hand anacron is for replacing what cron can't do when the machine is not powered on. Mostly is intended for personal desktop computers and laptops.

So we have crontab for CRON and anacrontab for ANACRON.

My questions:
1) each job that is in crontab and not runned because the machine is off...will anacron verify that has no been performed and run that task?

2) Or do i have to add my script to the folder

/etc/cron.hourly
/etc/cron.daily
/etc/cron.weekly
/etc/cron..monthly

that is specified in the anacrontab?

3) or add an extra line to anacrontab like this

15 20 backup /home/user/scripts/./mybackupscript

So the task has to be perform every 15 days 20 mins after the OS boot?

For what i understand if the 15th day the machined is not powered anacron will perform the task the first time that the computer powers on after that day, checking that the job has no been executed according to the anacrontab.

I am wrong?

Thanx and sorry for my bad english speeling.

PD: The cron mail output to user@localhost will work the same in anacron or will have to be specified like in crontab. Maybe adding MAILTO=user@localhost to the anacrontab

---

### Post by Jussi Kukkonen on 2006-09-14
> 1) each job that is in crontab and not runned because the machine is off...will anacron verify that has no been performed and run that task?
No. Anacron doesn't check cron jobs, as far as I know. Remove the cron jobs, and add same jobs in anacrontab (your option three).
> 15 20 backup /home/user/scripts/./mybackupscript

So the task has to be perform every 15 days 20 mins after the OS boot?

For what i understand if the 15th day the machined is not powered anacron will perform the task the first time that the computer powers on after that day, checking that the job has no been executed according to the anacrontab.

I am wrong?
Close. It's every fifteen days (with a 20 minute delay before execution), otherwise exactly as you described. 
EDIT: actually, now that I read your sentence again, it seems you got it exactly right. I just misunderstood you :)

I'm not sure about the mail output.

---

### Post by subzero79 on 2006-09-14
Ok thank u.

So what happens to the srcipts that are in the default anacrontab folder like cron.daily cron.weekly , etc. These folder contains scripts named cvs, man-db, popularity-contest(no idea what that script does), etc,etc. Do these tasks actually perform? or a i can delete these files?

thanx

---

