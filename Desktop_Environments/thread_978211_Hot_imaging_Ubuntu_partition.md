---
title: "Hot imaging Ubuntu partition"
date: 2008-11-10
forum: Desktop Environments
---

### Post by sionghua on 2008-11-10
Hi all,

Is there anything equivalent to DriveImageXML ([http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)) that can hot image the ubuntu partitions while it is on? This is for scheduled backup of the OS for restoration in case it breaks in future. Heard about rsync and tar, are they able to restore the partition when it breaks?

Thanks.

---

### Post by cdtech on 2008-11-10
Yes, both "rsync" and "tar" can restore the partition. I personally use "tar" as my backup solution. Using a bash script I wrote, I do a full, incremental, and a monthly backup. The incremental backups are of any changes to the system since last backup (using a date variable).

---

### Post by sionghua on 2008-11-11
Hi, I have tried successfully to manually use tar to backup Ubuntu, can you share your script file with me? I want to automate the backup process. Thanks.

---

### Post by Zack McCool on 2008-11-11
Personally, I take a different approach.  YMMV.

I like rsnapshot.  It backs up all data and configuration files 4 times per day, and retains backups in a GFS system.  So, I have backups in the following increments:

4 for today
1 for each day this week
1 for each week this month
1 for each month for the past 6 months

This does not backup the OS.  IMO, that is unneeded, especially if you stick to the packages in the repository.  You can reinstall cleanly and quickly from the LiveCD, and use AptOnCD to get all of the packages you use backed up.  A full reinstall takes about 30 minutes, including all of your packages, then you restore your data, and any config files you want.  

It is a bit more complex than an image, but it is not hard, and if you end up screing something up on your own, this doesn't restore your screwups...   ;)

As for a ghost-type image on the fly, I don't know of any app that does that in Linux.

Tar or rsync will backup everything on the fly, but if you have a hard drive failure, you'll still need to create the partitions on your own, so at least be sure to keep a note around with your partitions and sizes on it...

---

### Post by Zack McCool on 2008-11-14
Not sure if you still care or not, but an answer to your question was posted as a howto recently.  It doesn't work through any gui, and takes a little work to set up, but once you take the time, it is very handy...

[http://ubuntuforums.org/showthread.php?t=581680]("http://ubuntuforums.org/showthread.php?t=581680")

If you need help with the specifics, let me know.  I put together a script on my machine to test it out, and after modifying it to fit my personal disk structure, I found it to work wonderfully...

---

