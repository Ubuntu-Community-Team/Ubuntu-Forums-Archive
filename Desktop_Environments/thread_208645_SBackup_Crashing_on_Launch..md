---
title: "SBackup Crashing on Launch."
date: 2006-07-03
forum: Desktop Environments
---

### Post by AlphaMack on 2006-07-03
For some reason Simple Backup Config will not launch at all.  In the Terminal, I get this message:

```
Traceback (most recent call last):
  File "/usr/sbin/simple-backup-config", line 681, in ?
    i = SBConf()
  File "/usr/sbin/simple-backup-config", line 200, in __init__
    self.widgets.get_widget("time_hour").set_value( int(croninfo[1]) )
ValueError: invalid literal for int(): *
jpalmeda@JPA-PowerBook:~$

```

The program worked until I saved my configuration.  I haven't been able to launch it from the System menu since.  I tried removing sbackup completely via Synaptic including config files and re-installing it without success.

How do I get sbackup working again?


Edit:  Duh.  Pesky file in /etc/cron.d.  Never mind.

---

### Post by Theo van Nee on 2006-07-04
High,
I have exactly the same problem. However very little Linux experience so can't help you. Hopefully somebody else comes up with a solution.
Regards,
Theo

---

### Post by AlphaMack on 2006-07-04
Try my suggestion in the edit by removing /etc/cron.d/sbackup.  I literally had my answer minutes after posting this thread.

---

### Post by Theo van Nee on 2006-07-05
Great, thank you, that worked.
But how did you find out?

---

