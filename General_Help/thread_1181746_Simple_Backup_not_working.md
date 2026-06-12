---
title: "Simple Backup not working?"
date: 2009-06-08
forum: General Help
---

### Post by Robbyx on 2009-06-08
I have installed Simple Backup. I have chosen the logarithmic purging.  Looking at the restore source folder it advises that the last full backup is Jan 09. These seems to be very out of date. Why is this? Do I have to manually start the backup ever time?

---

### Post by callan79 on 2009-06-08
> **Robbyx said:**
> I have installed Simple Backup. I have chosen the logarithmic purging.  Looking at the restore source folder it advises that the last full backup is Jan 09. These seems to be very out of date. Why is this? Do I have to manually start the backup ever time?


Hi Robbyx,

I just want to make sure you do have a schedule enabled too? The logarithmic stuff really just relates to how long backups are retained.

What do you have set up on the 'time' tab?

I do recall reading about a bug where the backups don't happen if you set a SPECIFIC time.

Personally mine are set to "simply" and "daily". Everything works great.

What settings are you using?

Cheers
CD

---

### Post by Robbyx on 2009-06-08
These are settings which appear not to work:

Daily backups
Simply at 4
Full backup at least once every 7 days

---

### Post by Robbyx on 2009-06-11
Any chance of some further advice as to why SB does not appear to be working?

---

### Post by callan79 on 2009-06-12
> **Robbyx said:**
> These are settings which appear not to work:
Daily backups
Simply at 4
Full backup at least once every 7 days



Hi Robbyx,

Whoops, forgot to reply - sorry about that!

Re the SimpleBackups .... I've checked mine to work out how the schedule works. Remember I have mine set to "daily - simply" which means it'll do it once a day regardless of time.

I just get this entry within the /etc/cron.daily/ directory :

```

lrwxrwxrwx 1 root root   26 2009-05-23 17:40 sbackup -> /usr/share/sbackup/sbackup

```

So this just means it executes 'sbackup' daily.

Now if you've got it set to 4pm, you must have it set to 'precisely' and not 'simply', right?

So can you post the output of :

```

crontab -l
sudo crontab -l -u root

```

Then we can find out if you have a CRON set up.

I just tried changing mine to 'precisely 4am' and I get a new file called /etc/cron.d/sbackup and it contains :

```

0 4 * * *	root	if [ -x /usr/sbin/sbackupd ]; then /usr/sbin/sbackupd; fi;

```

Does this file exist on your system?

Cheers
Callan

---

### Post by Robbyx on 2009-06-12
Re the SimpleBackups .... 
> 
I just get this entry within the /etc/cron.daily/ directory :

```

lrwxrwxrwx 1 root root   26 2009-05-23 17:40 sbackup -> /usr/share/sbackup/sbackup

```

this just means it executes 'sbackup' daily.

I can not see that entry but there is as file called sbackup within /etc/cron.daily ie /etc/cron.daily/sbackup. It only contains:

if [ -x /usr/sbin/sbackupd ]
then /usr/sbin/sbackupd
fi

Now if you've got it set to 4pm, you must have it set to 'precisely' and not 'simply', right?

So can you post the output of :

```

crontab -l

mine is:
0 0,4,8,12,16,20 * * *	/usr/local/bin/ubuntuzilla.py -p thunderbird -a checkforupdategui 2>&1 | logger -p user.notice -t "UBUNTUZILLA" -- 

> 
sudo crontab -l -u root


rob@rob-desktop:~$ sudo crontab -l -u root
[sudo] password for rob: 
no crontab for root
rob@rob-desktop:~$ 

> 
Then we can find out if you have a CRON set up.

I just tried changing mine to 'precisely 4am' and I get a new file called /etc/cron.d/sbackup and it contains :

[code]
0 4 * * *	root	if [ -x /usr/sbin/sbackupd ]; then /usr/sbin/sbackupd; fi;

```

Does this file exist on your system?

Yes but the contents are not the same as yours. See above

---

### Post by callan79 on 2009-06-13
> Yes but the contents are not the same as yours. See above


Hi Rob,

So in /etc/cron.d/ you don't have a file called 'sbackup' ? In theory you should, however the 0 4 * * * may look diffrent.

Can you try changing your Simple Backups to "daily" and "simply" ?

If you do this, you should get this entry within the /etc/cron.daily/ directory:

```

lrwxrwxrwx 1 root root   26 2009-05-23 17:40 sbackup -> /usr/share/sbackup/sbackup

```

and it should all work. Can you try?

Cheers
Callan

---

### Post by Robbyx on 2009-06-15
> **callan79 said:**
> Hi Rob,

So in /etc/cron.d/ you don't have a file called 'sbackup' ? In theory you should, however the 0 4 * * * may look diffrent.

Can you try changing your Simple Backups to "daily" and "simply" ?

If you do this, you should get this entry within the /etc/cron.daily/ directory:

```

lrwxrwxrwx 1 root root   26 2009-05-23 17:40 sbackup -> /usr/share/sbackup/sbackup

```

and it should all work. Can you try?

Cheers
Callan


I have changed to daily and simply but the sbackup file in cron.daily only shows:

#!/bin/bash
#
# Sbackup Service file used by anacron

if [ -x /usr/sbin/sbackupd ]
then /usr/sbin/sbackupd
fi

Based on what I can see in the restore program it has not done a full backup since January.

---

### Post by callan79 on 2009-06-16
> **Robbyx said:**
> I have changed to daily and simply but the sbackup file in cron.daily only shows:

#!/bin/bash
#
# Sbackup Service file used by anacron

if [ -x /usr/sbin/sbackupd ]
then /usr/sbin/sbackupd
fi




Perfect - that's the same as mine.

To expand on that, /etc/cron.daily/sbackup is actually a link to the "real" /usr/share/sbackup/sbackup, which contains all the stuff you quoted above.

So now, the backups should work.

If not, can you quote and /quote, and paste a copy of your /etc/sbackup.conf. You'll need sudo for that.

For the record, here's mine :

> 
callan@brutis:/etc$ sudo cat sbackup.conf 
[sudo] password for callan: 
[exclude]
regex = \.mp3,\.avi,\.mpeg,\.mpg,\.mkv,\.ogg,\.ogm,\.tmp,/home/[^/]+?/\.thumbnails/,/home/[^/]+?/\.Trash,/home/[^/]+?/\..+/[cC]ache,/home/[^/]+?/\.gvfs/
maxsize = -1

[places]
prefix = /usr

[dirconfig]
/proc/ = 0
/sys/ = 0
/var/ = 1
/var/cache/ = 0
/tmp/ = 0
/dev/ = 0
/home/ = 1
/var/tmp/ = 0
/media/shared/Essentials/ = 0
/media/shared/ = 1
/media/shared/Utils/ = 0
/media/shared/Backups/ = 0
/usr/local/ = 1
/etc/ = 1

[general]
stop_if_no_target = 0
target = /media/wags/Backups/SimpleBackup
format = 1
purge = log
maxincrement = 60
lockfile = /var/lock/sbackup.lock




Hear from you soon!

Cheers
Callan

---

### Post by Robbyx on 2009-06-16
Mine isn't exactly the same. Which should I alter? 

The target = /media/g/backup
   There is no space on this drive, but  I thought this would not matter because sbackup is supposed to clear space by deleting old backups.

 Within the backup folder are a number of files but their excludes, packages and partitions are empty.  The most recent are May 3 and 22, June 3 and 13.

The following have files.tgz: Jan 23, May 22,

The other 2009 backups are empty.

Robin 



> [exclude]
regex = \.mp3,\.avi,\.mpeg,\.mkv,\.ogg,\.iso,/home/[^/]+?/\.thumbnails/,/home/[^/]+?/\.Trash,/home/[^/]+?/\..+/[cC]ache,/home/[^/]+?/\.gvfs/
maxsize = 10485760

[places]
prefix = /usr

[dirconfig]
/media/ = 0
/media/mydocs/ = 1
/var/cache/ = 0
/var/ = 1
/home/ = 1
/var/spool/ = 0
/var/tmp/ = 0
/usr/local/ = 1
/etc/ = 1

[general]
stop_if_no_target = 0
target = /media/g/backup
format = 1
purge = log
maxincrement = 7
lockfile = /var/lock/sbackup.lock

---

### Post by callan79 on 2009-06-16
> **Robbyx said:**
> There is no space on this drive, but  I thought this would not matter because sbackup is supposed to clear space by deleting old backups.



Yes it will, however the policy is something like - one day from last week, one week from last month, one month from last year. So this means that your backups don't actually delete that often.

Suggest you free up some space and see if that solves it first.

Let us know?

Cheers
Callan

---

### Post by Robbyx on 2009-06-21
> **callan79 said:**
> Yes it will, however the policy is something like - one day from last week, one week from last month, one month from last year. So this means that your backups don't actually delete that often.

Suggest you free up some space and see if that solves it first.

Let us know?

Cheers
Callan

Thank you it is solved. 

I moved the backup to a drive with more space and now it is working properly. I have some of the old backups on the other partition. Do you know what I need to copy over to have the old backups integrated into the new location? Apart from the ful folders  there as a srestore.desktop  file. I suspect this file is not important because the new location has only ful and inc folders nothing else. Just checking.

Robin

---

### Post by callan79 on 2009-06-21
> **Robbyx said:**
> Do you know what I need to copy over to have the old backups integrated into the new location? Apart from the ful folders  there as a srestore.desktop  file.


Hi Robbyx,

I don't think you need the srestore.desktop file ... just the actual backup folders.

Cheers
Callan

---

### Post by to-im-flow on 2009-06-25
Hey guys!

I just tried sbackup for the first time. I used the default settings but chose a USB-stick as destination.

When I click "backup now!" it just says "Backup run initiated in the background. ID blabla." Nothing else. Is that all? When do I know it's done? At least I can see that it created a folder on my stick with a few files.

The default settings are just a part of the whole system. Is that really enough to restore the whole system if something's wrong? 
I also tried to include every folder of the system (exclude zero) but then I can see nothing on my stick although it also says "backup run initiated...". 

Sorry this may sound totally stupid but I'm new and just don't get it.

Cheeers!

---

### Post by Robbyx on 2009-06-25
I suggest you give it a day and see if there is a file there ending in ful. The easiest way is to choose a file under the restore option. You can then see how far the back has progressed. The full backups end in .ful and the incremental in .inc

Have you checked your data files are included in the backup options. The default may not be sufficient if you are filing in a non standard area such as a separate hard disk.

---

