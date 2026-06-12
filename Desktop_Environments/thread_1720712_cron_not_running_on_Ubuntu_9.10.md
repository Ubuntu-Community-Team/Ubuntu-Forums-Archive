---
title: "cron not running on Ubuntu 9.10"
date: 2011-04-03
forum: Desktop Environments
---

### Post by arkobose on 2011-04-03
Hello,
After saving a few sample scripts in crontab, I discovered that cron is not running properly on my Ubuntu 9.10 (32 bit), after a recent reinstallation. Please note that the files "/var/log/cron" and "/etc/defaults/rc.conf" are empty in my system.

Any help would be greatly appreciated! Thank you!

---

### Post by mister_p_1998 on 2011-04-04
I had that once on Gutsy, I only cured it by a wipe and re-install. Hope you manage to cure it.
Might be worth completely removing cron & reinstalling
Steve

---

### Post by arkobose on 2011-04-05
I removed cron completely, and reinstalled it, but the problem remains as it is. Am all ears, everyone!

Thanks!

---

### Post by hictio on 2011-04-05
This might seem obvious, but, is the cron service/ daemon actually running?
```

ps auxw | egrep cron

```

Also:
```

/etc/init.d/cron status

```

---

### Post by mörgæs on 2011-04-05
At the end of the month 9.10 is out of support, and you (we, that is...) must install another release. 

Rather than trying to solve your problem now and install 10.04 / 10.10 later I would recommend installing the new release first and focus on cron after that.

---

