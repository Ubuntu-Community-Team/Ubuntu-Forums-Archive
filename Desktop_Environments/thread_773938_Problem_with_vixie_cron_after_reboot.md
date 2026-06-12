---
title: "Problem with vixie cron after reboot"
date: 2008-04-29
forum: Desktop Environments
---

### Post by viric on 2008-04-29
Hello,

I use Ubuntu Desktop 7.10, and I don't know how to get my user crontab working after reboot.
I have a ready crontab file (written using crontab -e) which has a task to be run every minute (* * * * *). It works well after editing the crontab. But when I reboot the system, the task is not done until I do a "crontab -e" again, writing the changes, although I change nothing in the file.
After that, the cron job is run again, every minute.

Of course, I'd like the cron job to be run even if I don't do a "crontab -e; save" after every reboot.

Can you experience something similar? I don't think it's related to any special configuration...

Regards,
Lluís.

---

### Post by Doctor-No on 2011-03-08
Hey, I have the same problem on my server.
After each reboot all users have to modificate (crontab -e; save) their crontabs to get them working again.
Did you or anyone else find a solution for this problem?

---

### Post by Doctor-No on 2011-03-08
SOLVED (for me):
Cron wasn't started on system boot.

Fix:
```

update-rc.d cron defaults

```

---

