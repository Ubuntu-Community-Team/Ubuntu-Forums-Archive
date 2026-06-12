---
title: "wtmp log and ssh restart"
date: 2006-07-30
forum: Desktop Environments
---

### Post by matko on 2006-07-30
hello. ssh disconnect me very often.

dont know why.
this is my auth.log
> Jul 30 05:53:23 matko sudo:    matko : TTY=pts/2 ; PWD=/var/log/apache2 ; USER=root ; COMMAND=/usr/bin/nano audit_log
Jul 30 05:54:14 matko sudo:    matko : TTY=pts/2 ; PWD=/var/log/apache2 ; USER=root ; COMMAND=/usr/bin/nano audit_log2
Jul 30 05:54:25 matko sudo:    matko : TTY=pts/2 ; PWD=/var/log/apache2 ; USER=root ; COMMAND=/usr/bin/nano error.log
Jul 30 06:01:16 matko sshd[7367]: Accepted password for matko from 195.28.102.214 port 1773 ssh2
Jul 30 06:01:16 matko sshd[7369]: (pam_unix) session opened for user matko by (uid=0)
Jul 30 06:01:25 matko sudo:    matko : TTY=pts/3 ; PWD=/home/matko ; USER=root ; COMMAND=/usr/bin/nano /var/run/klogd/kmsg
Jul 30 06:01:31 matko sshd[7369]: (pam_unix) session closed for user matko
Jul 30 06:01:43 matko sshd[7388]: Accepted password for matko from 195.28.102.214 port 1775 ssh2
Jul 30 06:01:43 matko sshd[7390]: (pam_unix) session opened for user matko by (uid=0)
Jul 30 06:01:59 matko sudo:    matko : TTY=pts/3 ; PWD=/home/matko ; USER=root ; COMMAND=/usr/bin/nano /var/log/syslog


could zou tell me why please? i think it happens everz time cron is started. is it possible? where can i find cron jobs? thanx.

another question is if you know why I cant find mz wtmp log.
i dont have it? is anz howto for this log?
i am looking for script that will find all errors and failed authentification and other "bad" stuff ;) do you know any?
**anybody tell me what tips and usefull hints you know about logging. I AM PARANOIC. :)**


[FONT="Arial Black"][COLOR="Red"][SIZE="4"]UBUNTU ROCKS[/SIZE][/COLOR][/FONT]

---

### Post by jpkotta on 2006-07-30
You can read wtmp (which for some stupid reason is in binary) with the last command.```
last
```

Cronjobs are located in /etc/cron.d, and also each user (including root) has a crontab file.  You can read the crontab files with ```
crontab -l
```

---

