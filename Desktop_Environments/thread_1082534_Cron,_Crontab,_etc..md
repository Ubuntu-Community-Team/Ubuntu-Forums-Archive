---
title: "Cron, Crontab, etc."
date: 2009-02-27
forum: Desktop Environments
---

### Post by luigi_mb on 2009-02-27
Running Ubuntu 8.10 on ThinkPad T61 with 4GB RAM.

Running 

```
crontab -u luigi -l
```

I get an empty list. Ditto with 

```
sudo cron -u root -l 
```

Having installed f-prot, I can verify that the virus def list is indeed regularly updated. Shouldn't crontab list the corresponding ask?

Where are tasks located? 
Are there other ways to set up scheduled tasks?
Is "at" the only way to do so?

Thanks.

/luigi

---

### Post by hictio on 2009-02-27
I don't have installed but, is it updated daily? Then my guess is that you should check for the script on the '/etc/cron.daily/' directory; check the other directories if its executed hourly, etc.

---

### Post by luigi_mb on 2009-02-28
> **hictio said:**
> I don't have installed but, is it updated daily? Then my guess is that you should check for the script on the '/etc/cron.daily/' directory; check the other directories if its executed hourly, etc.

I can see lots of entries under cron.hourly, cron.daily, etc. And I can read the contents of /etc/crontab , where I did find a single entry, for f-prot.  I still do not understand why crontab itself does not display this item and all the other items. 

Thus my question is: is it possible to list all the scheduled tasks? How?

Thanks.

/luigi

---

### Post by pparks1 on 2009-02-28
Well, each user has a crontab file..as you saw when you ran crontab -u username.

The system also has many cronjobs that are found in /etc/crontab that also run.   They are cron.daily, cron.hourly, cron.weekly and cron.monthly.  Each has a subfolder which can contain any number of scripts and these run based on the times specified in the /etc/crontab file.

As far as I know, you will just have to look in both places...your user account and /etc/crontab to see what is going to be run under cron.   I don't know of a way to show absolutely everything together all in one place.

---

### Post by luigi_mb on 2009-02-28
> **pparks1 said:**
> Well, each user has a crontab file..as you saw when you ran crontab -u username.

The system also has many cronjobs that are found in /etc/crontab that also run.   They are cron.daily, cron.hourly, cron.weekly and cron.monthly.  Each has a subfolder which can contain any number of scripts and these run based on the times specified in the /etc/crontab file.

As far as I know, you will just have to look in both places...your user account and /etc/crontab to see what is going to be run under cron.   I don't know of a way to show absolutely everything together all in one place.

Yes, I can see and examine all the scripts in the /etc/cron.*/ folders. Too bad there seems to be no way to show them in one easily browsable place. I wonder whether anybody ever wrote something that would do so.

Until then, I thank you all for your prompt and generous help, and if nobody objects maybe we can consider this thread closed.

/luigi

---

