---
title: "Automatich mysql backup"
date: 2009-04-25
forum: General Help
---

### Post by Tobia on 2009-04-25
Hello,
I must change a mysql backup configuration in a little server. I did not setup this by myself, so i don't know where to find this configuration. It is a daily mysql dump, i checked every cron file in /etc (crontab, cron.daily, cron.d) but i did not find nothing, where I should lock for?

Thanks

---

### Post by Brucevdk on 2009-04-25
> **Tobia said:**
> Hello,
I must change a mysql backup configuration in a little server. I did not setup this by myself, so i don't know where to find this configuration. It is a daily mysql dump, i checked every cron file in /etc (crontab, cron.daily, cron.d) but i did not find nothing, where I should lock for?

I believe personal crontabs (also for the root user) are stored in /var/spool/cron/crontabs/. The usual way to edit them though is by invoking *crontab -e* as the relevant user. You can always do a system wide grep by executing: *grep -i -R "mysqldump" /*

---

### Post by geirha on 2009-04-25
```
sudo crontab -l
```

---

