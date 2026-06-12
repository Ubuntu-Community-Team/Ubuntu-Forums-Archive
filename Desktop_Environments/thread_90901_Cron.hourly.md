---
title: "Cron.hourly"
date: 2005-11-16
forum: Desktop Environments
---

### Post by Eleka on 2005-11-16
Hello people!

I'm tring to put a script in /etc/cron.hourly for be runned one time at hour, but, only moving the script into the directory doesn't work.

Are something to do apart of move the script into the /etc/cron.hourly? (It's a python script)

---

### Post by vruum on 2005-11-16
make sure the script is executable, "sudo chmod +x script" and that it has, on the first line "#!/usr/bin/python"

---

### Post by Eleka on 2005-11-16
Yeah, I will test ... it is executable, but don't have #!/usr/bin/python on the first line

---

### Post by Eleka on 2005-11-16
I can't get it working ... I add the line #!/usr/bin/python at the beginning of the script, but it doesn't work.

Have I to restart the cron demon or something similar to take changes effect?

---

### Post by Kyral on 2005-11-16
cron.hourly is for system scripts. You'd have to edit your own crontab

---

### Post by gts on 2006-01-13
> cron.hourly is for system scripts. You'd have to edit your own crontab

What do you intend for system scripts? I have the same problem: I've tried to put a script dynIP.sh (a dynamic dns script that has to be executed as root) in /etc/cron.hourly... I've also tried to edit /etc/crontab:


# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
56 *    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.hourly
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#




[email]root@antares:/etc/cron.hour[/email]ly# ls -l
totale 4
-rwxr-xr-x  1 root root 613 2005-12-30 22:15 dynIP.sh
[email]root@antares:/etc/cron.hour[/email]ly#


Nothing seems to work... My script is never executed...

---

