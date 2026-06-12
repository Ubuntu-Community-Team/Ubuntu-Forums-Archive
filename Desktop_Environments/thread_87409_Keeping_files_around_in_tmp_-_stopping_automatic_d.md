---
title: "Keeping files around in /tmp - stopping automatic deletion"
date: 2005-11-08
forum: Desktop Environments
---

### Post by matiasp on 2005-11-08
Hi there,
Something is automatically deleting files under /tmp, leaving at any time only files that are hours' long. I actually want to keep files there for longer or delete them manually.

I checked the crontab for root as well as all the scripts under /etc/cron.d and nothing seems to refer /tmp at all.

Any ideas as to what's deleting things from /tmp?

Thanks,
matias

---

### Post by Remmelas on 2005-11-08
open /etc/init.d/bootclean.sh in your favorite editor and go to line 131
and delete it

---

