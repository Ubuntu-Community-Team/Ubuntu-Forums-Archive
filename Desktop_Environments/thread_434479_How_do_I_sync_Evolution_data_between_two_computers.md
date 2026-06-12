---
title: "How do I sync Evolution data between two computers?"
date: 2007-05-06
forum: Desktop Environments
---

### Post by flloyd on 2007-05-06
Hi, I have both a desktop and a laptop that I would like to use Evolution on. However, I cannot figure out how I am supposed to sync Evolution data between these two computers. I would like for them to both have the same contacts, calendar, tasks, etc. Is this possible? The only thing I have found is to sync it with a Palm Pilot but I don't have one of those. Thanks for any responses.

---

### Post by flloyd on 2007-05-07
Does this ability really not exist? How do corporate users use Evolution in multi-computer environments?

---

### Post by amoore on 2007-05-07
You need an M$ exchange server or (a  free serverless solution) would be to use gmail and [www.scheduleworld.com](www.scheduleworld.com) but the instructions to use the sync client for scheduleworld.com are a little complicated. 

I would recommend using an M$ exchange server but the free method works well too.  If you go the free route, I would install the sync client for scheduleworld.com  and use a cron job to sync automatically every 15mins.

instructions for to sync client for scheduleworld.com are at [http://ubuntuforums.org/showthread.php?t=282408]("http://ubuntuforums.org/showthread.php?t=282408")
I would highly suggest you read the whole post. It took me a couple of try until I got it working right. 

Also, Kcron is great for setting up the cron job to sync automatically once you have the  sync client working.

Good luck.

---

### Post by rhodry on 2007-05-07
Assuming you can network the two machines together successfully and have all repos enabled; I would recommend mounting the relevant drive/folder  from the other machine, then use either 'rsync' or 'unison' to syncronise between the two. 

Have a look at 'man rsync' & 'man unison' for details. Both are in the repos and are powerful tools that can be used at the command line or in cron jobs. I think rsync has a graphical frontend called 'grsync' or something like that. Do an aptitude cache search on rsync and you will find it.

Cheers,
Paul.

---

### Post by flloyd on 2007-05-07
Okay, thanks for the input. I was hoping that there was going to be an easier way. I can't believe that Evolution doesn't have a plugin that allows for this ability (say by syncing with an ftp or WebDAV server).

I'll take a look at your suggestions when I have more time later this week. Hopefully if I have any questions I can get some help.

Once again, thanks a bunch.

---

### Post by Luke22 on 2007-07-02
> **rhodry said:**
> I would recommend mounting the relevant drive/folder  from the other machine, then use either 'rsync' or 'unison' to syncronise between the two. 

Hi Paul,

I tried this as I was interested in the same simple server-less synchronisation and it turns out that evolution saves an ID for each task entry in the file .evolution/tasks/local/system/tasks.ics where the tasks are listed. This ID includes the computer name and probably is the reason, why my laptop tasks did not show up on my desktop task list of Evolution after copying the .evolution folder. I only looked at tasks, so I don't know what the situation is with the rest like emails etc.

It seems that a simple synchronisation of the .evolution folder is not enough.

If anybody finds more info on this, please let us know.

Thanks,
Luke

---

### Post by tgm4883 on 2007-07-17
I vaguely remember multisync having the ability to sync evolution to a backup folder.  Perhaps you can sync multiple computer to this backup folder?

I cannot check this as I no longer use multisync.  I was using it to sync evolution to a wince device, but now I have a palm.

---

### Post by VSpike on 2007-07-18
If you are mainly interested in email sync, you can run your own IMAP server locally, like dovecot or courier-imap.  I run dovecot + maildrop + postfix + clamav + spamassassin, and can access my email my work laptop using Outlook Express (yuck, but probably the most solid IMAP client for Windows).

All my mails and folders (including drafts and sent items) are kept in the IMAP server, so I see the same folders from anywhere.

Next step is to try and get a webmail solution running, and also get ScheduleWorld and syncevolution going to see if I can sync PIM data between systems including my Pocket PC.

---

### Post by defishguy on 2007-07-18
I'd give [Conduit]("http://gnomefiles.org/app.php/Conduit") a try.  It looks like the Swiss Army Knife of synchronization.

Good luck!

---

