---
title: "10pm Disk Thrash"
date: 2009-04-01
forum: General Help
---

### Post by kdt_denton on 2009-04-01
Hi, everyone, thanx in advance for any help ...

OK .. so every night at exactly 10pm the hard disk goes absolutely bug$hit for about 5-10 minutes, thrashing to the extent that the mouse slows down on the screen.

Can't see anything here that is set to launch at 10pm every night.

Ideas?

See my sig below for the specs on my machine.

here is the version:
```

Linux kdt-lnx0 2.6.24-23-generic #1 SMP Mon Jan 26 01:04:16 UTC 2009 x86_64 GNU/Linux

```

here is /etc/crontab
```

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

```

---

### Post by ryanhaigh on 2009-04-02
I would suggest using the command iotop to determine what is causing all the disk activity. According to ubuntu package search it is only available for intrepid on but you could try installing the deb in hardy (from your sig). 

[apt://iotop]("apt://iotop")

---

### Post by jo4hnc on 2009-04-02
Can't you use System Monitor to do the same thing?

System>Administration>System Monitor. Then click on the processes tab.

---

### Post by Yashiro on 2009-04-02
Probably your logs getting compressed and rotated.
Perhaps you have some issues that's causing a log file to get very large, hence this process is causing problems.

---

