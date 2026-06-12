---
title: "grsync rsync with cron ???"
date: 2009-06-22
forum: General Help
---

### Post by measekite on 2009-06-22
**Assumption: ** Using Jaunty you schedule 3 backup jobs.  One at 1, the next at 2 and the last at 3.  

The first job runs at 1 for 30 minutes.  The second job runs at 2 and last for one and a half hours and does not finish until 3:30.

**Question:**
Does the last job run 30 minutes late after the second job completes or does it start on time and both are backing up at the same time multitasking (like they should) or does the last job never run since is could not start at 3 since the second job was still going.
[B]
Comments:[/B]
If that is true then grsnc-rsync-cron has a problem since one never knows how long a job will take as as data grows you need to keep chainging the times.

---

