---
title: "Log, Temp and Garbage files?"
date: 2005-05-22
forum: Desktop Environments
---

### Post by grakhul on 2005-05-22
Ok here is my question:  
In windows I had to remove temp files, I had to perform disccleanup, I had to defrag.
I understand that Ubuntu does not need to be fragged.  But LOG files in /var/log these are getting big and are getting zipped.  
1. Can I remove these log files?
2. can I just delete the zipped versions and the *.log files?
3. What will happen if I just deleted all files in this directory?  rm /var/log/*
4. Where can I specify the size of log files?
5. Cron is running on my system, I know it automates processes.  Anyone know of a good guide to turning it off or tweaking it?  I dont think it should be running.
6.  /tmp has lots of stuff in it too.  Things like orbit-localhost and lots of other files and   directories with giberish.  Can I delete everything here too?  There are some things that look important in the /tmp directory.
7.  I want to be able to limit the size of any files that is keeping track of  my system metrics.  Anyone know of a lists that tells me what is being written and logged? (/var/messages  /var/log/boot and things like this)

---

### Post by agger on 2005-05-23
[QUOTE=grakhul]Ok here is my question:  
1. Can I remove these log files?
2. can I just delete the zipped versions and the *.log files?
3. What will happen if I just deleted all files in this directory?  rm /var/log/*
[/QUOTE]
Yes, the system will recreate them when needed. Note, however, that it shouldn't be necessary to do this, not very often, anyway. How large a percentage do they take up of your disk? 
I think it should be quite safe to remove all files in that directory, though

[QUOTE=grakhul]

5. Cron is running on my system, I know it automates processes.  Anyone know of a good guide to turning it off or tweaking it?  I dont think it should be running.
6.  /tmp has lots of stuff in it too.  Things like orbit-localhost and lots of other files and   directories with giberish.  Can I delete everything here too?  There are some things that look important in the /tmp directory.
7.  I want to be able to limit the size of any files that is keeping track of  my system metrics.  Anyone know of a lists that tells me what is being written and logged? (/var/messages  /var/log/boot and things like this)[/QUOTE]

I don't think actually stopping cron is a good idea, you might need it some day ... If you want to know if it's scheduling something right now try typing 

sudo crontab -e

 in a terminal window (type "man crontab" in another terminal window for help interpreting the lines in the crontab file).

The files in /tmp may be used by running programs, and you should not delete them indsicriminately. "Well-behaved" programs are supposed to clean up their temporary files. If the directory grows to an unmanageable size, don't delete recent files - delete only files that haven't been modified for (say) a couple of days or so.

---

### Post by grakhul on 2005-05-23
Thanks

---

