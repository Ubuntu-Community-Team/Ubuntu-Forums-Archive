---
title: "Waking up"
date: 2005-11-08
forum: Desktop Environments
---

### Post by netguardianii on 2005-11-08
Under Ubuntu, is it possible to programmatically wake up from standby? For instance, could I wake up my laptop at a certain time? I've searched high and low on Google for this, but I can't seem to find anything. I know that this can be done under Windows by implementing CreateWaitableTimer.

---

### Post by Qrk on 2005-11-08
You need a cron daemon. 

Lucky for you Ubuntu already has one. You just need to install a frontend to manange it.

```
sudo apt-get install gcrontab
```

I haven't used it since warty, but I remember it being somewhat unfriendly in the UI sense.

---

### Post by netguardianii on 2005-11-08
I'm not sure, but would a cron daemon still function when the system is in standby?

And also, did you mean, "crontab"? I've actually attempted to use it to execute a shell script, but I got some weird results instead.

---

