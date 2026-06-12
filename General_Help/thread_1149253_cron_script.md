---
title: "cron script"
date: 2009-05-05
forum: General Help
---

### Post by catarano on 2009-05-05
Can anybody please pass me a script to clean the /tmp and /var/tmp directories at startup?
thanks a lot

---

### Post by spacesamurai on 2009-05-05
If what you want is a script that will remove the files on start-up, that is different than using the cron function. The cron function executes scripts at a specified time. Which one do you want?

---

### Post by dcstar on 2009-05-05
> **catarano said:**
> Can anybody please pass me a script to clean the /tmp and /var/tmp directories at startup?
thanks a lot

/tmp is automatically cleared at startup, all files that are in there are required for the current session.

---

### Post by slakkie on 2009-05-05
> **spacesamurai said:**
> If what you want is a script that will remove the files on start-up, that is different than using the cron function. The cron function executes scripts at a specified time. Which one do you want?

Under BSD you could have @boot entries in your crontab, don't know if Ubuntu/Linux has the same..

---

### Post by catarano on 2009-05-05
what about /var/tmp ?

---

### Post by catarano on 2009-05-05
> **spacesamurai said:**
> If what you want is a script that will remove the files on start-up, that is different than using the cron function. The cron function executes scripts at a specified time. Which one do you want?

actually i would like both functions to work
have both directories cleared at startup and also have some scripts that check that files older than let' s say 1 day are deleted...

---

### Post by slakkie on 2009-05-05
> **catarano said:**
> actually i would like both functions to work
have both directories cleared at startup and also have some scripts that check that files older than let' s say 1 day are deleted...

Your script could look like this, all files older then 1 day are removed. However, /var/tmp is usually used for temp data that must be kept even if the machine reboots, so removing data from that dir might not be the best idea. Maybe remove files older then 1 month is a better idea.

```

for i in /tmp /var/tmp ; do
    find $i -mtime +1 -exec rm {} \;
    # One month old data has to be removed
    #find $i -mtime +31 -exec rm {} \;    
done

```

---

### Post by legatek on 2009-05-05
> **slakkie said:**
> Under BSD you could have @boot entries in your crontab, don't know if Ubuntu/Linux has the same..

Ubuntu uses @reboot.

---

### Post by catarano on 2009-05-05
> **slakkie said:**
> Your script could look like this, all files older then 1 day are removed. However, /var/tmp is usually used for temp data that must be kept even if the machine reboots, so removing data from that dir might not be the best idea. Maybe remove files older then 1 month is a better idea.

```

for i in /tmp /var/tmp ; do
    find $i -mtime +1 -exec rm {} \;
    # One month old data has to be removed
    #find $i -mtime +31 -exec rm {} \;    
done

```

thank you
maybe i will make two scripts one for /tmp (1 day) and another for /var/tmp (31 days)

---

