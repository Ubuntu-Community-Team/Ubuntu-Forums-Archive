---
title: "What is the best way to setup an auto-backup to an external HD"
date: 2007-06-03
forum: Desktop Effects &amp; Customization
---

### Post by Rocket2DMn on 2007-06-03
I am trying to figure out the best method of automatically backing up specific files and directories to a backup folder on my large external USB harddrive.  I know about rsync but I think that is for network backup only.
Obviously, I don't want to backup files that haven't changed since the last backup.
Suggestions?

---

### Post by majed on 2007-06-03
Try this link...

[http://www.debianhelp.co.uk/backuptools.htm]("http://www.debianhelp.co.uk/backuptools.htm")

I use another set of scripts to do exactly what u want, but i'm not on my laptop now and so i can't remember where i got them from, but they are neat.. i found them online and customized them a bit..

---

### Post by keithweddell on 2007-06-03
Rsync can do this on a single machine - it doesn't have to work over a network.  I wrapped it in a bash script that collects the data I want (eg mysql dumps) and then rsyncs to a separate harddrive.  It still needs some tidying up but it runs over night from cron.  You might need to look at udev rules to get a consistent predictable mount point for your external drive.

Keith

---

### Post by majed on 2007-06-03
> **majed said:**
> Try this link...

[http://www.debianhelp.co.uk/backuptools.htm]("http://www.debianhelp.co.uk/backuptools.htm")

I use another set of scripts to do exactly what u want, but i'm not on my laptop now and so i can't remember where i got them from, but they are neat.. i found them online and customized them a bit..


I am home now and this is the script i was talking about:

[http://www.linux-backup.net/scripts/pepas.sh.txt]("http://www.linux-backup.net/scripts/pepas.sh.txt")

Use this text file to generate 3 files.. the backup.sh script, the whattobackup and the whatnottobackup files.

You can then use cron to automatically schedule the job or you can have a launcher (like the one I did and attached) to manually start the script..

Attached are my customized files for your reference. I run the launcher.sh script with sudo.

PS: i changed the name of the two files appending .txt so i can upload them.

Regards,
Majed

---

### Post by Rocket2DMn on 2007-06-03
Thanks a lot majed, I'll edit the scripts to my needs and give it a try in a few days when I have the time.

---

