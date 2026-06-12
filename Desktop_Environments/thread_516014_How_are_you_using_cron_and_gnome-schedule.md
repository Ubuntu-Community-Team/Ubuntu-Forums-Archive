---
title: "How are you using cron and gnome-schedule?"
date: 2007-08-02
forum: Desktop Environments
---

### Post by eeefresh on 2007-08-02
I have been reading about scheduling tasks with gnome-schedule or cron.  It looks pretty neat, but I am not sure how I would use it.  In Windows I might use a similar program to defragment at a certain time of day, but that's not necessary in Linux.

How else can I use this tool?  So for those of you that are scheduling tasks, what are they?

---

### Post by goodfella on 2007-08-02
I use cron and resync to back up my home directory, as well as my windows documents and mp3's.

---

### Post by eeefresh on 2007-08-03
Thanks, goodfella.  Any other ideas?  I also thought about using it to run a virus scanner each night, but I am not sure if that is even necessary in Linux.

---

### Post by measekite on 2008-01-07
> **goodfella said:**
> I use cron and resync to back up my home directory, as well as my windows documents and mp3's.

I want to do exactly that but am having difficulty.  I do not know cron but have installed and tried to use gnome schedule.  For one thing I cannot edit the time.  It appears that I have to enter the entire thing again.  There also seems to be problems when you save a template and then use the advanced tab to set the hour and minute you want the job to run.

Basically for the command I do this:

rsync -what ever options  source destination

but it does not appear to run.

What I did was copy the rsync command line from grsync and paste it into gnome schedule.

Any help would be appreciated.

---

