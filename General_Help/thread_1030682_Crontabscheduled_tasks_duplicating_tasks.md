---
title: "Crontab/scheduled tasks duplicating tasks"
date: 2009-01-04
forum: General Help
---

### Post by lsutiger on 2009-01-04
I have a strange one here.

I have three entries in crontab. One set to run @ 6:30am, next @ 9:30am and the last @ 9:35.

The one set to run @ 6:30 is running at 6:10 and at 6:30.

There is nothing listed when I sudo crontab -e.

I have no idea why this is happening...could someone try to help me out?
thanx!

---

### Post by dcstar on 2009-01-04
> **lsutiger said:**
> I have a strange one here.

I have three entries in crontab. One set to run @ 6:30am, next @ 9:30am and the last @ 9:35.

The one set to run @ 6:30 is running at 6:10 and at 6:30.

There is nothing listed when I sudo crontab -e.


The how do you know "I have three entries in crontab"?

Please list these entries.

---

### Post by lsutiger on 2009-01-04
When I enter crontab -e this is what I get:```
30 9 * * 0,2-6 copyall #JOB_ID_3
30 6 * * 0,2-6 ./di #JOB_ID_1
35 9 * * * ./ip #JOB_ID_2

```
When I eneter sudo crontab -e there is nothing listed.

---

### Post by jpkotta on 2009-01-04
You should probably give an absolute path to the commands you are executing from cron.  Your time specs look OK.

Each user has an independent cron table; when you run crontab, it access the crontab for the user you run it as.  So unless you do a 
```
sudo crontab -e
``` and add some entries for root's crontab, of course it will be empty.  There are also system cron entries in /etc/cron.{hourly,daily,weekly,monthly}, and these are run as root.  They are independent of root's crontab.

---

### Post by lsutiger on 2009-01-04
Thanx for the response. All scripts are in my home folder. But nothing said explains how to correct this. There are only two users on my system, root, and my profile.

---

### Post by lsutiger on 2009-01-06
I found duplicates in /etc/cron/weekly.

Do not know how they got there...but thanx for the reply!

---

### Post by mike2357 on 2009-01-06
Regular users can have their own cron commands, as can root, even though the cron daemon process is run by root.

crontab -e  is to display and edit cron commands for the user who invoked the command.

sudo crontab -e is to display and edit cron commands for root.

---

### Post by dcstar on 2009-01-06
> **lsutiger said:**
> When I enter crontab -e this is what I get:```
30 9 * * 0,2-6 copyall #JOB_ID_3
30 6 * * 0,2-6 ./di #JOB_ID_1
35 9 * * * ./ip #JOB_ID_2

```
When I eneter sudo crontab -e there is nothing listed.

When you want to list things, use:
```
crontab -l
```
There is no need to use the editor to view crontab entries, you risk accidentally changing things.

---

### Post by lsutiger on 2009-01-09
Aww crap!

OK, I am little confused over all of this. Could someone please explain in detail how crontab, cron.weekly, cron.monthly, cron.daily, cron.d and system-->preferences-->scheduled tasks are related?

I now have only two of the three tasks running that are set in scheduled tasks, which are also reflected in crontab -l

I think it may have had something to do with the duplicates I had deleted in cron.weekly

Thanx in advance!!!

---

### Post by mike2357 on 2009-01-09
Maybe I have a few thoughts to help get you started.  Let's start by defining two sets of commands:
cron  -- for scheduled tasks that run off the clock
anacron -- for scheduled tasks that run off the clock with the ability to invoke jobs sooner if your computer has been down for awhile.  For instance, if your computer was down when a monthly task was supposed to kick in, you don't have to wait until next month.

Obviously at this point you're wanting to use anacron, but my advice is to learn by using cron.  It's a lot easier to get to know.  When you've worked up a healthy comfort level, you can, if you choose, come back and learn about anacron.

So to answer your question, cron.weekly, cron.monthly and cron.daily are used by your system for its housekeeping tasks via anacron.  So if you're going to take my advice and start with cron, you can ignore them.  Likewise, you can just leave the cron.d directory alone unless you have some special configuration needs.

That leaves crontab.  Every user can have their own crontab file.  The files are stored in /var/spool/cron/crontabs, but you never want to modify them directly.  Instead, use the "crontab -e" command to modify them and "crontab -l" to list their contents.  If you're logged in as yourself, just run "crontab -e" as yourself, and when the cron commands kick in, it will be as if you are running it yourself.  Likewise, if a cron command needs root permissions, then run "sudo crontab -e" to modify root's crontab file.

Enough to at least clear some of the haze?

You can run "man 5 crontab" for a wealth of information about the contents of crontab files.

As to your question about "scheduled tasks", I can't help you there.

Good luck.  Cron can be a bit picky, but is kind of fun to use.  It also is a good example of the power of Linux/Unix.

Feel free to post back if you have a follow-up question.

---

### Post by jpkotta on 2009-01-09
As I understand it, the /etc/cron.{hourly,daily,weekly,monthly}/ directories work as follows.  You put a script in the directory corresponding to the time interval you want.  The system crontab has entries for each of these directories.  So at 17 minutes after the hour, every hour, a cronjob is run that executes each of the scripts in cron.hourly.  Similar for the others.  It could be done by just adding each script to the system crontab (/etc/crontab), but it's a bit nicer to put a script into a directory and run them all at once (assuming you only care about the period, not the precise time that they are run).

---

### Post by lsutiger on 2009-01-10
Thanx for all of the replies!
I am still having a problem. I am reposting my crontab:```
15 6 * * 0,2-6 copyall #JOB_ID_3 (this one is not working)
30 6 * * 0,2-6 ./di #JOB_ID_1
35 9 * * * ./ip #JOB_ID_2
00 9 * * * copyall #JOB_ID_4

```

Here is the cron.log:```
Jan 10 06:15:01 brian-linux /USR/SBIN/CRON[9164]: (brian) CMD (copyall #JOB_ID_3)
Jan 10 06:17:01 brian-linux /USR/SBIN/CRON[9341]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 10 06:25:01 brian-linux /USR/SBIN/CRON[10043]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Jan 10 06:30:01 brian-linux /USR/SBIN/CRON[10484]: (brian) CMD (./di #JOB_ID_1)

```

As you can see from the log, the task is running, but I am not getting th results. This task has been running consistently for approximately 8 months and started having problems a couple of weeks ago.


The ./di is in the home folder and does work, the copyall is in my /home/<user>/bin folder and is executable. The folder is listed in my path, so I can run it from anywhere by just typing copyall<enter>

This is just throwing me for a loop. What other info could I give to help me figure this out?

Thanx in advance!

---

### Post by mike2357 on 2009-01-10
Try changing
```
copyall
```
to
```
copyall >| OUT_COPY 2>&1
```

This will send output, including error messages, to a file called OUT_COPY.  After the cron command runs, you can check OUT_COPY for clues.

You could also try using a full path to "copyall".  Often cron runs with an abbreviated PATH.

---

### Post by lsutiger on 2009-01-10
ok mike! changed  in crontab, will know results in morning!

---

### Post by dcstar on 2009-01-10
> **lsutiger said:**
> 
.......
The ./di is in the home folder and does work, the copyall is in my /home/<user>/bin folder and is executable. The folder is listed in my path, so I can run it from anywhere by just typing copyall<enter>
......

Cron jobs do NOT run in the same environment as a user shell.

As is recommended in almost every HOWTO on cron jobs, put in the **absolute path** to all commands.

---

### Post by lsutiger on 2009-01-10
> **dcstar said:**
> Cron jobs do NOT run in the same environment as a user shell.

As is recommended in almost every HOWTO on cron jobs, put in the **absolute path** to all commands.

Hmmm..as I said before, all of these have been running for months with no problem. This probelm just showed it's face abou 2 weeks ago.

---

