---
title: "Question on apt-get clean and apt-get autoclean"
date: 2009-06-19
forum: General Help
---

### Post by JockVSJock on 2009-06-19
Apt-get clean and apt-get autoclean both do a little housekeeping, however does autoclean do a bit better job then apt-get clean?  I've noticed that apt-get autoclean is part of the daily apt cron job.  

Is it true that if you don't use dselect for package management that you should run these often?  

thanks

---

### Post by mc4man on 2009-06-19
from man apt-get
 > clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(8 ) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

       autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.


---

