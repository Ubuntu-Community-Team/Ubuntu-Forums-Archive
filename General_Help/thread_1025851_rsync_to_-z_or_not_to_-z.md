---
title: "rsync: to -z or not to -z ?"
date: 2008-12-30
forum: General Help
---

### Post by max_power on 2008-12-30
I have a 1TB drive and i want to back up about 800GB from various windows servers. 

Im writing a script that will run via cron. This script will attach to each server via smbfs, run rsync, then unmount. 

My question is, should i be using the -z (compression) switch for the back ups? If so, how does that effect the restoration process if a file needs to be restored?

Thanks,

---

