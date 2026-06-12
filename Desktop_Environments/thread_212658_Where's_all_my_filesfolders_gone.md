---
title: "Where's all my files/folders gone?"
date: 2006-07-10
forum: Desktop Environments
---

### Post by petersjm on 2006-07-10
Hi all,

I have just had to reinstall both Windows and Ubuntu 6.06 on my drive. Now I can't find all the folders that began with a period (like .mozilla-thunderbird etc). Do you know where they could be? I thought they were in the root or home folder, but the only thing in there is the Desktop and my automatix.log file.

Oh, a second question, if I can... When I partitioned the drive during the Ubuntu install, it asked me how big to make the new partition. I only have a 40Gb drive, so I gave it 30Gb. Now in Nautilus, it says the root folder only has 6Gb and it's "Unable to mount" the remaining 30Gb partition. I thought I was making the 30Gb partition for Ubuntu. Any way I can access it?

PS - I'm a noob, so talk slowly :D

---

### Post by AZzKikR on 2006-07-10
Perhaps this is just a stupid suggestion... :D but in Nautilus you can view hidden files/folders (those which start with a period) by pressing CTRL-H. Within a terminal/console you can list hidden files/folders using the command
```
ls -la
```

---

### Post by petersjm on 2006-07-10
Hmmm. Thanks, AZzKikR, I tried CTRL+H and that worked. I had clicked "Show Hidden and Backup Folders" in Preferences, and thought that was enough. CTRL+H did it. Nice one, thanks a lot :D

Now for my second question (above)... :)

---

### Post by AZzKikR on 2006-07-10
CTRL+H is actually the hotkey to 'Show Hidden and Backup Folders', so I find it weird that checking that box didn't work for you!

For your second question, try installing gparted and check how the partitions look like. Perhaps the partition was unformatted? Just an idea.

---

### Post by petersjm on 2006-07-10
Thanks again, AZzKikR, but I'm afraid I wouldn't have a clue how to use gparted... :S 

Anyway, I'm leaving the country in an hour or two so it can wait until I'm back. Thanks a lot of your help.

---

