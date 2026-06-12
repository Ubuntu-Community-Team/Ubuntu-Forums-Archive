---
title: "Question about Cron/Backups"
date: 2009-04-22
forum: General Help
---

### Post by jwbrase on 2009-04-22
Can cron jobs be set up so that if the computer is off at the time scheduled for the job (Or any other condition applies that could prevent the job from taking place), it will be delayed until the next boot/shutdown/screensaver activation or other convenient time?

My Dad wants to do automated backups, but has been having trouble finding a method that works well with how we operate our computers. The programs he's found do their backups at a rigidly scheduled time, and we generally shut our computers off for the night, which means that if we schedule backups at night and forget to leave the computer on on a night when it will be backed up, the backup job ends up being missed. If we schedule it in the daytime, it interferes with use of the machine. The ideal solution would be that, once a backup job came due, the machine would wait until the next time the user initiated a shutdown and perform the backup then, delaying the shutdown until it was finished. Would this be doable with a sufficiently well put together cron job? Are there any backup programs that can do anything like this?

---

### Post by James_Lochhead on 2009-04-22
My suggestion would be to have a script (based on [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)) do a back-up for you and then switch the computer off. The script would just be a couple of lines.

You could then put it on the Desktop of each user that uses the computer and make it executable. It would then be a question of the last user to use the computer just clicking on the script and selecting run rather than shutting down normally.

---

### Post by KyleBrandt on 2009-04-22
What you want to read about is [run levels]("http://en.wikipedia.org/wiki/Runlevel").  When you shutdown a system you set it to run level 0 , scripts in /etc/rc0.d will be executed.  'Best practice' is not to put the scripts there, but create them in /etc/init.d and use update-rc.d to create symlinks for whatever runlevel.   

-Kyle

---

