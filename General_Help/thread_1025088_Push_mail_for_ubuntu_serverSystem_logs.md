---
title: "Push mail for ubuntu server/System logs"
date: 2008-12-29
forum: General Help
---

### Post by djanie78 on 2008-12-29
Am looking at having push mail on my ubuntu server. Any ideas on where to look please??? Thanks.

Right this is a tricky one. I had my server running for weeks with no trouble.Remote administer it via SSH and webmin with no issues. Then all of a sudden i couldnt log in. With a quick phone call, i got the system restarted. All good now. Is there i way or a log i can see what happened before i restarted the system???
All i wanna know is why i could log in the first time and had to restart it. Any help please?

Thanks

---

### Post by eBoxNet on 2008-12-29
all system logs are stored in /var/log directory
here is a list of log files :


=> /var/log/messages : General log messages

=> /var/log/boot : System boot log

=> /var/log/debug : Debugging log messages

=> /var/log/auth.log : User login and authentication logs

=> /var/log/daemon.log : Running services such as squid, ntpd and others log message to this file

/var/log/dmesg : Linux kernel ring buffer log

/var/log/dpkg.log : All binary package log includes package installation and other information

/var/log/faillog : User failed login log file

/var/log/kern.log : Kernel log file

/var/log/lpr.log : Printer log file

/var/log/mail.* : All mail server message log files

/var/log/mysql.* : MySQL server log file

/var/log/user.log : All userlevel logs

/var/log/xorg.0.log : X.org log file

/var/log/apache2/* : Apache web server log files directory

/var/log/lighttpd/* : Lighttpd web server log files directory

/var/log/fsck/* : fsck command log

/var/log/apport.log : Application crash report / log file

---

### Post by eBoxNet on 2008-12-29
you could also use this link to read how to mail a log file using cronjob : 

[http://ubuntuforums.org/showthread.php?t=608766](http://ubuntuforums.org/showthread.php?t=608766)

---

### Post by dcstar on 2008-12-29
> **eBoxNet said:**
> you could also use this link to read how to mail a log file using cronjob : 

[http://ubuntuforums.org/showthread.php?t=608766](http://ubuntuforums.org/showthread.php?t=608766)

Why bother when the **logcheck** package is designed to do this sort of thing?

---

### Post by eBoxNet on 2008-12-29
didn't know,sorry

---

