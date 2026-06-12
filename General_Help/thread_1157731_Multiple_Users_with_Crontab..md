---
title: "Multiple Users with Crontab."
date: 2009-05-13
forum: General Help
---

### Post by Roasted on 2009-05-13
Just a quick question... say you have 2 hard drives in your computer. The 2nd is just simply an rsync backup of the main one, where your home directory gets backed up.

BUT - you have 2 users with specific rights to each home directory. How can you set up crontab to run your rsync script at a specific time if the other user is logged in?

If I set crontab to run "fredsbackup" as the user "fred" while bob is still logged in, will it run?

EDIT - I know I can run it as root. But I'm trying to run these tasks at the user level only.

---

### Post by dcstar on 2009-05-13
> **Roasted said:**
> Just a quick question... say you have 2 hard drives in your computer. The 2nd is just simply an rsync backup of the main one, where your home directory gets backed up.

BUT - you have 2 users with specific rights to each home directory. How can you set up crontab to run your rsync script at a specific time if the other user is logged in?

If I set crontab to run "fredsbackup" as the user "fred" while bob is still logged in, will it run?

EDIT - I know I can run it as root. But I'm trying to run these tasks at the user level only.

User cron jobs don't care about other users, you should have separate cron jobs for backing up each /home folder to avoid any permissions issues if you are not allowing root to do them all (which makes more sense).

---

### Post by djurny on 2009-05-13
you could fiddle around with 'users' command and filter the currently logged on users from rsync script. let rsync backup /home, reading that rsync is in a cronjob it runs as root.. use rsync options to preserve all permissions and you should be set to go..

something like:
```

cd /home && rsync $(users|sort -u|xargs -n1 printf "--exclude=""%s""\n") . /srv/storage/backup

```

---

### Post by Roasted on 2009-05-13
I was thinking about this.

rsync -a --delete /home/fred /media/backup

Run this @ 3 am via crontab with the user "fred"





rsync -a --delete /home/bob /media/backup

Run this @ 3:30 am via crontab with the user "bob"


Question was, if Bob is logged in, will Fred's execute? That was my only concern.

---

