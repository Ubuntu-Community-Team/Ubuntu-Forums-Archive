---
title: "/etc/cron.daily won't run..."
date: 2009-05-23
forum: General Help
---

### Post by Denbert on 2009-05-23
Hi,

Im trying to setup a daily cronjob in order to stop my vmware guest OS, copy to backup folder, and then start the vmware guest OS again.

The script runs great from the command line, see code below:
```

#!/bin/sh

# Suspend VMs rather than shutting them down
# Guy Leech 10/08/07

# Scipt that shut down all VM => Backup to a place => and start all VM
# modified by Siegfried Marechal 03/10/08

# Where the VM are
VMDIR="/virtual_machines/*"

# Backup directory
BACKUPDIR="/vmbackup/"

# Don't forget to specifie password at lines 21 and 31 ********

cd $VMDIR

        find . -type f -name \*.vmx -printf '[standard] %p\n' | sed 's/ .\// /' | while read LINE
        do
                echo Stoping $LINE ...
                 vmrun -T server -u root -p password -h https://127.0.0.1:8333/sdk stop "$LINE"
        done


cp -R $VMDIR $BACKUPDIR

find . -type f -name \*.vmx -printf '[standard] %p\n' | sed 's/ .\// /' | while read LINE
        do
                echo Starting $LINE ...
                 vmrun -T server -u root -p password -h https://127.0.0.1:8333/sdk start "$LINE"
        done
```


File is in /etc/cron.daily and has this name **vmware-backup**

the owner and group is **root:root**

chmod is **755** similar to all the other cronjob files in the /etc/cron.daily folder.

anyone who can point me in correct direction?

---

