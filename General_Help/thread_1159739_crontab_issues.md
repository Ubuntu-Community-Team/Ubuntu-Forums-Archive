---
title: "crontab issues"
date: 2009-05-15
forum: General Help
---

### Post by reggler on 2009-05-15
Hi There,

I wrote a little shell script that is 5 t8imes pinging google.com and verifying if at least 3 pings went thru, if not I'm restarting NetworkManager - this needs to be done as root so i went 
# sudo - s
# crontab -e
and entered 
01 * * * *  /root/myscript.sh

and my script is writing some data into a buffer file "/root/result" anf i "ls -l" in /root/ i don't see the time refreshed every minute, why not? my script should be called every 1 minute.... what am i doing wrongly? If I manually call the script, the time gets refreshed... :o

Thanks for help!

---

### Post by reggler on 2009-05-15
ah I think i got it just by looking at it, i should go like * * * * * in cron tab unless it gets executed in the the first minute of every hour, eh?
Yup, that's right :)

---

### Post by gamblor01 on 2009-05-15
Have you actually started cron though?  Try:

```

sudo /etc/init.d/cron start

```If so, it looks like your entry only runs once/hour (at one minute past the hour).

Edit: Yep, looks like you already figured that out.

---

### Post by reggler on 2009-05-15
> **gamblor01 said:**
> Have you actually started cron though?  Try:

```

sudo /etc/init.d/cron start

```

If so, it looks like your entry only runs once/day...at 12:01am.

yup, with ```
* * * * *
``` it seems to be working fine! :) Time of "/root/result" gets refreshed every minute! :)

---

