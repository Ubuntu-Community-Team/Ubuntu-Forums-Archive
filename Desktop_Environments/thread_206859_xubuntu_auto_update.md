---
title: "xubuntu auto update"
date: 2006-06-30
forum: Desktop Environments
---

### Post by drlock on 2006-06-30
I have recently installed xubunut on two machines and it is running beautifully.  However on both machines I have noticed that auto update does not seem to work.

I have gone into Applications->System->Software Properties and set Internet Updates to check automatically, but I still haven't been notified of any updates (I know there are updates because my Ubuntu system at work tells me about them).  I can check for updates manually, but it would be nice to get the auto updater working.

Am I missing something or does xubuntu just not support this?

Thanks

---

### Post by EPOX123 on 2006-12-07
I think it doesn't support it, suck isn't there a plugin or some thing?

---

### Post by drlock on 2006-12-07
I just saw some discussion on the xubuntu-dev mailing list talking about adding this for Feisty. From the discussion it sounded like it would not be hard to do, but I still haven't figured it out.

---

### Post by dannyboy79 on 2006-12-07
you could always just add a daily cron job, sudo aptitude update && sudo aptitude upgrade. i simply just remember to do this every once in awhile since I use x on my old laptop.

---

### Post by kast on 2007-08-07
Question, when i set up the aptitude update and upgrade in cron being that i need to sudo to get it to install the upgrades how do i do that? Sorry if i worded that wrong :)

---

### Post by drlock on 2007-08-10
First, let me warn you that putting 'apt upgrade' in crontab is a little dangerous.  Once in a great while an upgrade will break something.  When something breaks it usually helps in diagnosis if you know that you just upgraded and what packages you upgraded.

If you still want to, you can add it to /etc/crontab
You will notice that there is a column in that file for setting the user the command will run as, so just make sure you specify root and then you won't need sudo.
For more details on cran tab read the man page crontab(5)
```
man 5 crontab
```

---

### Post by fbianconi on 2008-05-20
> First, let me warn you that putting 'apt upgrade' in crontab is a little dangerous. Once in a great while an upgrade will break something. When something breaks it usually helps in diagnosis if you know that you just upgraded and what packages you upgraded.
I agree.

There's /etc/cron.daily/apt script for that, but doesn't work out of the box. You should
```

sudo chown root:admin /var/lib/apt/periodic/update-stamp
sudo chmod g+w /var/lib/apt/periodic/update-stamp

```
That is untested don't try it yet.
In principle should work, but not guarantee (yet).

edit --
It works, just be sure to be run either cron or anacron

edit 2--
**I was wrong it do work out of the box**. there's not need to chown that file, **just be sure to be running cron or anacron.**

---

