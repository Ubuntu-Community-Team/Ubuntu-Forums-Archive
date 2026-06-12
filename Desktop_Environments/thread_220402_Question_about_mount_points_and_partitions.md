---
title: "Question about mount points and partitions"
date: 2006-07-21
forum: Desktop Environments
---

### Post by jimbren on 2006-07-21
Got a silly question...

I'm running Dapper on a laptop with an external 250GB HDD connected via USB. The USB drive has two partitions--200GB for .mp3 files and 50 for backing up my /home directory.  I've created two directories, /mp3 and /backups, within my / directory and have my fstab file set to mount them on startup when the drive is connected to the laptop.  

If I'm going to be using the laptop away from the drive for an extended period of time, I have gotten into the habit of commenting out those two mount points from my fstab file.  That way, I don't get error messages the next time I boot and the laptop is disconnected from the USB drive.

I also have rsync running a nightly backup of /home.

This morning I booted up and got the following error when I tried to log into KDE: warning: unable to write to /tmp; X session may exit with an error"

I cleaned out my apt cache and was able to login without any problems, but I was very surprised to learn that my / partition was full.  

In thinking this through, I think that my problem arises from the fact that I have /mp3 and /backups listed in fstab, and that I comment them out when I don't want to see errors.  Am I right in assuming that when the system boots with the /mp3 and /backups lines commented out of my fstab file, the system is thinking of them as normal directories without mount points on their own partition?

Should I be manually mounting these drives when I connect the USB drive instead of how I'm doing it right now?

I think in writing this out I've answered the question for myself, but I'd like to get some input from someone smarter than me.  Maybe some better ideas, too.

Thanks,

jimbo.

---

### Post by reacocard on 2006-07-21
if there is nothing mounted there, it is treated as a normal folder. probably what happened is rsync kept backing up to the /backup directory, and filled up your disk. mounting it manually instead shouldn't change anything. what you need to do is tell rsunc not to backup when the drive is not mounted. idk how you'd do that though.

---

### Post by suhaswadkar on 2006-07-21
> **jimbren said:**
>  I think that my problem arises from the fact that I have /mp3 and /backups listed in fstab, and that I comment them out when I don't want to see errors.  Am I right in assuming that when the system boots with the /mp3 and /backups lines commented out of my fstab file, the system is thinking of them as normal directories without mount points on their own partition?



    wow, really stupmed there. I'm not 100% sure, but when u don't mount ur external HDD, /mp3 & /backup don't get locked or anything. whatever u copy or backup in these directories, it gets stored in ur notebook's HDD. Besically all dir are part of / tree. if & when u mount /mp3 & /backup on external HDD, it is used. And if not then internal HDD is used.

---

### Post by jimbren on 2006-07-21
I suppose I could change the backup path within my rsync command to point to the full path instead of the mount point?  I don't think I'm wording it right...
so the mount point for /backups is:
```
/dev/sda2
```

and in my rsync command, it points to /backups.

instead of doing that, I could have rsync go to:
```
/dev/sda2
```

If the drive isn't mounted, the backup would fail instead of going to the root directory, which is fine.

Does that make sense?

I should just wait until I'm in front of my damn computer to check...

Thanks,

jim

---

