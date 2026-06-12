---
title: "Disk partition full"
date: 2009-03-21
forum: General Help
---

### Post by mikesmind on 2009-03-21
I have a problem with the partition I have set for /. (My /home is on another partitin.) It is showing full at 38.15GB in partition manager, but when I use Disk Usage Analyzer it shows 100% full at 2.6GB.  

I have an automated backup that runs daily and this filled up the partition.  I deleted several weeks of files and that should have freed up the space.  Is there something else I need to do to free up that space?

I am running Ubuntu 8.10.

Thanks, Mike

---

### Post by mikewhatever on 2009-03-21
2.6 Gb is not a lot for root. Can you post the output of <df -h>.
To free more space, run <sudo apt-get clean>and check the Trash bins.

---

### Post by RobtA on 2009-03-21
One possibility is that you moved numerous files to root Trash, rather than your user Trash. If so, they are still in the root Trash, which is not emptied when you empty your own Trash.

To empty root Trash, in Terminal:

sudo rm -rf /root/.local/share/Trash/

it will ask for your password, then permanently delete the root Trash files, if any are there. CAUTION: *sudo rm* is a powerful and dangerous tool.

---

### Post by mikesmind on 2009-03-21
Here is the output of <df -h>

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              38G   38G     0 100% /
tmpfs                 473M     0  473M   0% /lib/init/rw
varrun                473M  108K  473M   1% /var/run
varlock               473M     0  473M   0% /var/lock
udev                  473M  2.8M  470M   1% /dev
tmpfs                 473M  864K  472M   1% /dev/shm
lrm                   473M  2.0M  471M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda7              86G   13G   70G  15% /home
overflow              1.0M  1.0M     0 100% /tmp


Thanks, Mike

---

### Post by mikesmind on 2009-03-21
I logged in as root and emptied the root trash.  Here's my updated ,df -h

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              38G   12G   25G  33% /
tmpfs                 473M     0  473M   0% /lib/init/rw
varrun                473M  108K  473M   1% /var/run
varlock               473M     0  473M   0% /var/lock
udev                  473M  2.8M  470M   1% /dev
tmpfs                 473M  524K  472M   1% /dev/shm
lrm                   473M  2.0M  471M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda7              86G   13G   70G  15% /home
overflow              1.0M  1.0M     0 100% /tmp


Thanks, mikewhatever! It turned out to be a simple fix.

Mike

---

