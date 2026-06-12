---
title: "How do I run a program daily"
date: 2007-03-15
forum: Desktop Environments
---

### Post by niels on 2007-03-15
I have installed SyncEvolution, which synchronises Evolution with a SyncML server. It's working perfactly, but I have to run it from a console by hand.

Is it possible to make it run on a daily basis automaticly? I would like to run the command 'syncevolution scheduleworl' once a day. How do I do this?

If this is possible, what would happen if I do not use my computer for a day or more? And what if the computer is turned off at the time the synchornization is scheduled?

If it is not possible to schedule daily runs of the program, is it then possible to make a button somwhere which will do the job? How?

---

### Post by Dr. Nick on 2007-03-15
Ive never done this, so dont know the specifics, but you could probably use cron

[http://ubuntuforums.org/showthread.php?t=102626&highlight=cron](http://ubuntuforums.org/showthread.php?t=102626&highlight=cron)

---

### Post by Truespeed on 2007-03-15
In your /etc directory you'll find a folder called cron.daily.  Place a script within this directory to make your command run once per day.

example:

--- start of script--

#!/bin/sh

ls -l

-- end of script--

Save this in your cron.daily directory and it will run once per day.

You'll need to be a super user to add the file to the directory.  You may also need to issue the following command to set permissions:

chmod +rwxr [name of your file]

---

