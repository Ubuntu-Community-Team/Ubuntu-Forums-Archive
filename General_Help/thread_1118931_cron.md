---
title: "cron"
date: 2009-04-07
forum: General Help
---

### Post by measekite on 2009-04-07
I am using grsync over rsync and cron to automatically backup various folders at different times of the night.

Recently I have had a problem where some files do not appear to be backed up.  Previously they were.

**Question:  ):P**

1. Is there a log somewhere in the system that can show if and when cron ran and what it did?  I have multiple backup entries each hour from 1:00AM thru 5:00AM.

2. Is there something much better than cron that can do the same job?

---

### Post by Cheesehead on 2009-04-07
Take a look at the 'logger' command to add record of your scripts running (including cron jobs) to the log file of your choice.

---

### Post by measekite on 2009-04-08
> **Cheesehead said:**
> Take a look at the 'logger' command to add record of your scripts running (including cron jobs) to the log file of your choice.

Can you provide some details on just how to do that?

Thanks in advance

---

### Post by kpkeerthi on 2009-04-08
Just redirect the rsync output to file:
```

rsync -a /source /backup > /home/$USER/backup.log 2>&1

```

---

### Post by hyper_ch on 2009-04-08
you try to use grsync and cron?

---

