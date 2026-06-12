---
title: "Problem with CRON"
date: 2009-02-15
forum: General Help
---

### Post by solwic on 2009-02-15
I set up rsync and cron to play nicely together and make daily backups of all my useless junk.  This is the line in my cron file:

```
#run backup every day at 11pm
00 23 * * * rsync -va --delete /home/james/ /media/MyBook/RSyncBackup/ > /media/MyBook/RSyncBackup/backup.log

```

Which does, indeed, make a backup at 11:00 pm.  It just went through.  The CPU/Load went up in the monitor, the external HDD made its "I'm busy" writing noises, no problem at all. 

Except that I got no backup.log file, which I thought is what ```
... > /media/MyBook/RSyncBackup/backup.log
``` was supposed to do.  Did I miss something?  

This is my first time using both rsync and cron, so bear with me, please.  I tested that command by running it in terminal before I added it to cron, pointing the log file to be made on the desktop, and it worked.  

root is running that command...would that affect it?  

Thanks!

EDIT:  I just double checked all the paths and don't see any problems.  Was hoping it was that easy.... :(

---

### Post by solwic on 2009-02-16
This, my friends, is embarrassing.  The --delete flag tells the system to delete any file on the destination drive that does not exist on the source drive.  I have no backup.log in /home/james/, which means it's deleting backup.log from /media/MyBook/RSyncBackup/  

Duh.  

Thanks anyway.  Would mark solved if I could. 

I swear I'm an idiot. :oops:

---

### Post by solwic on 2009-02-16
Which leaves me with a problem.  How can I create a log file without removing the --delete flag?  

If I create an empty backup.log file in source, it copies the blank to destination and overwrites whatever it may or may not have created.  

Would this work?  

```
00 23 * * * rsync -va --delete /home/james/ /media/MyBook/RSyncBackup/ > /tmp/backup.log && mv /tmp/backup.log /media/MyBook/RSyncBackup/backup.log
```

??

Or is there a simpler way?

Thanks!

---

### Post by HermanAB on 2009-02-16
When using rsync do not specify the files to copy.  Tell it to copy everything with a wild card and then specify the files that should NOT be copied using the --exclude parameter.  See the man page.

In cron scripts, always specify the full path for a program, else it may not work, eg.  /usr/bin/rsync.

Hope that helps.

Herman

---

### Post by solwic on 2009-02-16
> **HermanAB said:**
> When using rsync do not specify the files to copy.  Tell it to copy everything with a wild card and then specify the files that should NOT be copied using the --exclude parameter.  See the man page.

In cron scripts, always specify the full path for a program, else it may not work, eg.  /usr/bin/rsync.

Hope that helps.

Herman

The trick though is that I want it to remove files from the destination that are no longer in the source.  If I list them individually I might as well remove them myself.  

In other words, I don't know what I want to exclude until I delete it, at which point I can add the backup copy to the rm command and save myself the hassle.

I'll look up the proper way to make a cron script, though.  I used a tutorial given to me, and it said to just add the one line.  I want to do it right.  :)

Thanks!

---

### Post by unutbu on 2009-02-16
```
00 23 * * * rsync -va --delete /home/james/ /media/MyBook/RSyncBackup/ > /media/MyBook/RSyncBackup.log
```
How about save the log outside of the RSyncBackup directory?

---

### Post by solwic on 2009-02-16
> **unutbu said:**
> ```
00 23 * * * rsync -va --delete /home/james/ /media/MyBook/RSyncBackup/ > /media/MyBook/RSyncBackup.log
```
How about save the log outside of the RSyncBackup directory?

That could work, couldn't it?  

Now I just have to learn how to make a proper cron script.  Google is my new friend.  

Thanks for stating the glaringly obvious.  :)

---

