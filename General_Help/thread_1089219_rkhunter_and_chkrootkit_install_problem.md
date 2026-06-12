---
title: "rkhunter and chkrootkit install problem"
date: 2009-03-06
forum: General Help
---

### Post by grubster on 2009-03-06
I have just installed rkhunter and chkrootkit but i cant see them in applications or system. Is this normal or should i be able to see them and configure them like a normal program?

---

### Post by dcstar on 2009-03-06
> **grubster said:**
> I have just installed rkhunter and chkrootkit but i cant see them in applications or system. Is this normal or should i be able to see them and configure them like a normal program?

They automatically run inside cron and e-mail the results to the root account.

Look in their man pages for configuration options.

---

### Post by grubster on 2009-03-06
thankyou

---

### Post by iaculallad on 2009-03-06
Additional Info:

You could run rkhunter from the terminal too:

```
sudo rkhunter -c --skip-keypress
```

and chkrootkit on [cron]("https://help.ubuntu.com/community/CronHowto#Crontab%20Example") by the Ubuntu Community (with additional information on cron jobs).

---

