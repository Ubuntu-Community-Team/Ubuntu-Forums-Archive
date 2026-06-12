---
title: "software management tool problem"
date: 2006-09-24
forum: Desktop Environments
---

### Post by lonelypauly on 2006-09-24
i clicked on the little orange icon just like i always do when an update is available, however, this time i got the following message:

"Only one software management tool is allowed to run at the same time.  Please close the other application e.g. 'aptitude' or 'synaptic' first.  so i am unable to get any updates until i fix this problem...and yes, i restarted my computer several times and the problem persists.

Im looking at the running processes right now and neither aptitude or synaptic are listed.  

Any ideas?

---

### Post by yage on 2006-09-24
Well something is locking up your system for sure... Have you tried ```
ps aux |grep aptitude
``` to see if its running? same for aptitude.<br>
You can also try ```
sudo apt-get update
``` and then if that works ```
sudo apt-get dist-upgrade
```Hope this helps you out ;)

---

### Post by lonelypauly on 2006-09-24
when i put in 'ps aux |grep aptitude' i got:

**6913  0.0  0.0   2876   796 pts/0    R+   09:33   0:00 grep aptitude**


when i put in 'sudo apt-get update' it appeared to be downloading the available updates but then i got the following message:

[B]Err [http://theli.free.fr](http://theli.free.fr) ./ Packages
  404 Not Found
Fetched 4B in 1s (3B/s)
Failed to fetch [http://theli.free.fr/packages/dapper/./Packages.gz](http://theli.free.fr/packages/dapper/./Packages.gz)  404 Not Found
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.[/B]

---

