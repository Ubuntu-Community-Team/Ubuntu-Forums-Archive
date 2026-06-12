---
title: "Scheduled Shutdown?"
date: 2005-12-20
forum: General Help
---

### Post by Video Toaster on 2005-12-20
Hi everyone!

I recently set up a computer with "Breezy Badger" and have been wondering if there was any way I could have my computer automatically shut down unattended at 5:00 PM (no user logged on).  Would this be relatively easy to do?

Thanks for any help you can give!  :D

---

### Post by briancurtin on 2005-12-20
you could do this using a cron job, assuming you know the proper commands on how to shut a system down. i personally dont know, but this is a/the way to do it.

```
man cron
```
that is your new friend

---

### Post by professor_chaos on 2005-12-20
the shutdown is "poweroff" and can be executed by sudo. You could try this with a cronjob

---

### Post by schilcha on 2005-12-21
Alternatively to the suggestions above, you can tell shutdown at what time to do so. 
```
sudo /sbin/shutdown -h 05:00
``` will power your machine off at 05:00. (I'm working in a 24-hour locale, so I don't care about am/pm -- check man shutdown for details). This approach is probably more handy, if you want to do this only once.

---

### Post by Video Toaster on 2005-12-25
Wow, thank you for your help!

If I use cron, will the scheduled event occur when I am logged off or only when I'm logged on?

---

### Post by professor_chaos on 2005-12-25
good question. I would guess that a cronjob for user A would only work when user A is logged in, but I am not sure. Put something like ```
01 01 * * * touch ~/cronlogouttest
``` and then logout a minute or two before that time and login after that time and look for the file in your home directory. That will answer the question.

---

### Post by Video Toaster on 2006-01-10
[QUOTE=schilcha]Alternatively to the suggestions above, you can tell shutdown at what time to do so. 
```
sudo /sbin/shutdown -h 05:00
``` will power your machine off at 05:00. (I'm working in a 24-hour locale, so I don't care about am/pm -- check man shutdown for details). This approach is probably more handy, if you want to do this only once.[/QUOTE]

The crontab exectues when I'm logged off!

However, will sudo work in a crontab since I can't type in my password to authenticate sudo?

Thanks so much for your help!

---

### Post by darth_vector on 2006-01-10
if you

sudo crontab -e

you edit the superusers crontab. here there is no need for using sudo, you can just put "/sbin/shutdown ..."

---

### Post by Video Toaster on 2006-03-17
OK, another question about crontab.  :D

I recently tried scheduling a clamscan job for midnight each day using root's crontab.

```
00 00 * * * clamscan <parameters>
```

However, when I check the log in the morning, all that is logged is the "Scan Started" header - the completion of the scan is never logged.  Why isn't clamscan finishing?  Is there another (better) way to do this?

Thanks again!  You're all a great help!

---

### Post by dcstar on 2006-03-17
[QUOTE=Video Toaster]OK, another question about crontab.  :D

I recently tried scheduling a clamscan job for midnight each day using root's crontab.

```
00 00 * * * clamscan <parameters>
```

However, when I check the log in the morning, all that is logged is the "Scan Started" header - the completion of the scan is never logged.  Why isn't clamscan finishing?  Is there another (better) way to do this?

Thanks again!  You're all a great help![/QUOTE]
It may be a bad idea to schedule jobs right on midnight, as other system things - like starting the next day's log file - might also be run at that exact time.

---

### Post by Video Toaster on 2006-03-18
[QUOTE=dcstar]It may be a bad idea to schedule jobs right on midnight, as other system things - like starting the next day's log file - might also be run at that exact time.[/QUOTE]
Hmm... I tried a bunch of different times, but each time it logs the start and then never actually finishes.

(I'd also like to note that nobody is logged on, just as I did with the shutdown thing)

---

