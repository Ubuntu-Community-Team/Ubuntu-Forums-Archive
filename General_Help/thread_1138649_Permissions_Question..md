---
title: "Permissions Question."
date: 2009-04-26
forum: General Help
---

### Post by Roasted on 2009-04-26
Here's a synopsis of my dilemma. There's a script I wrote that I want to run as myself without the use of sudo. But it's an rsync script. Currently I mount a backup drive (basically only used for network backups with other computers in the house) to /media/storage, and since that folder is owned by jason (myself) when mounted, I can simply run my backup script without sudo and it works fine.

That way, if the drive dies and does not get mounted, root would own the unmounted folder. What does this accomplish? If my backup script runs with the drive unmounted and I used "sudo" with the script, it would write data to the root partition and max it out - something I do NOT want. So it's important I run this script as myself.

But here's the curve ball... There's no way I can synchronize other users home directories to a second drive, is there? For example, right now I have 4 users set up with samba.

Jason
Fred
Jerry
Bob

Fred/Jerry/Bob synchronize to /media/storage, again owned by jason when mounted.

But if I were to purchase two 1TB drives and instead of having a dedicated network drive, just include them on the main TB drive, I wouldn't be able to synchronize their home directories to the backup TB drive, would I? 

Or can I just change the permissions of their home directories to 770 and add myself to the group? 

Does this all make sense?

---

### Post by antikristian on 2009-04-26
Well, there's probably several ways to do this. First, to avoid syncing when the disk is not mounted, you could add an if sentence into the script that checks wether the drive is mounted (cat mtab + some foo) or if a specific file is available that is only available on the drive.

Yes, yoo would be able to copy the files if you did this operation as yourself and with 770 permissions on the other users folders and files, you can also create an rsync user that is member of the respective users' group, and run the script with that user.

---

### Post by Roasted on 2009-04-27
Ehh, but if I ran rsync through an rsync user, wouldnt I have to be logged in as that user? The idea here is to have my computer act as a file server/backup server while still retaining basic functionality, which is why I want myself to be able to control this stuff. I already have it set up like that because I have an additional SATA drive in the PC for network storage, so I own the folder in /media it mounts to. I just wasn't sure how it would work with the home directories.

---

### Post by antikristian on 2009-04-27
if you want to execute a command with that user, you could just run ```
su username -c command
``` or start it automatically with cron

---

### Post by Roasted on 2009-04-27
Oh wait... yeah... I remember now cron had that option where it was "execute as..." and I had to put in my name.

Are you saying I could set up the scripts to simply run as "backup" (NOT Sudo Backup) under the designated user?

Examples:

Jason - 3:30AM - Backup
Fred - 4:00AM - Backup

If I'm logged in as Jason, idle, would the command @ 4:00 AM still execute as fred without sudo rights?

---

### Post by antikristian on 2009-04-27
If you add it to fred's crontab, then it will be executed as fred, even if he is not logged in at the time:)

Just run 
```
sudo crontab -u fred -e
```

And specify the command and time it should be run. remember to use absolute path to commands (/bin/cat not just cat)

to set up cron, check out [http://www.adminschoice.com/docs/crontab.htm#Example](http://www.adminschoice.com/docs/crontab.htm#Example)

---

### Post by Roasted on 2009-04-27
I have cron set up currently. I just didn't realize that while Jason is logged in, Fred could execute an automated command in cron. That's all. Thanks for the good tip!

---

### Post by antikristian on 2009-04-27
happy to help:)

---

