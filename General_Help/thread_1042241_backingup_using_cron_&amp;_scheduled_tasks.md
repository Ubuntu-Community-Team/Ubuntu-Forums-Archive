---
title: "backingup using cron &amp; scheduled tasks"
date: 2009-01-17
forum: General Help
---

### Post by alicemoon on 2009-01-17
I am using the following script to backup my thunderbird mail

#!/bin/sh
## Script to backup Thunderbird email
## Backup needs a date (stamp)
set -x
x=`date +%y%m%d.%H%M`
## Save space by making sure backup is archived
tar -cvzf "/media/WD USB 2/mailbackup/"${x}.tgz /home/street/.mozilla-thunderbird/

it works if I paste it directly into terminal but I would like to run it using scheduled tasks - I have placed it in a file and put the command
/home/street/scripts/mailbackupjdrive.sh 
into scheduled tasks however it does not work when I test it through the program - any help much appreciated

---

### Post by yoyoned on 2009-01-17
Cron needs absolute paths to the programs it runs

Example: Use /usr/bin/date instead of just date

---

### Post by lykwydchykyn on 2009-01-17
> **alicemoon said:**
> I am using the following script to backup my thunderbird mail

#!/bin/sh
## Script to backup Thunderbird email
## Backup needs a date (stamp)
set -x
x=`date +%y%m%d.%H%M`
## Save space by making sure backup is archived
tar -cvzf "/media/WD USB 2/mailbackup/"${x}.tgz /home/street/.mozilla-thunderbird/

it works if I paste it directly into terminal but I would like to run it using scheduled tasks - I have placed it in a file and put the command
/home/street/scripts/mailbackupjdrive.sh 
into scheduled tasks however it does not work when I test it through the program - any help much appreciated

 - Do you have execute permissions on the script?
 - Can you change the command in scheduled tasks to:
```

/home/street/scripts/mailbackupjdrive.sh &> /home/street/mailbackuplog.log

```

Then run it and check that file for errors.
 - You might want to change the first line to:
```

#!/bin/bash

```
To see if that helps.  I'm not sure if /bin/sh (a symlink to /bin/dash) sets all the same environment variables (most pertinently, the $PATH variable).

 - If none of that works, try using the full path on all the executable commands.

---

### Post by alicemoon on 2009-01-17
many thanks for both replies - I reset the permission on the script file using nautilus as root and now it is working:)
however when I added in the script for the logfile it was created but is empty - does this mean I still have a problem?

---

### Post by lykwydchykyn on 2009-01-17
That's odd... I'd have expected tar to have output, since you specified the -v flag.  Maybe the &> redirect isn't doing what I think it does.  Fancy redirect stuff always turns my head around.

---

