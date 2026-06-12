---
title: "cron.daily not running"
date: 2009-02-16
forum: General Help
---

### Post by nemesis256 on 2009-02-16
Last week I installed a new script to backup my database, and it doesn't seem to be running.  The script is [AutoMySQLBackup]("http://sourceforge.net/projects/automysqlbackup/"), and I put it in /etc/cron.daily with permissions as 0755.  

I can run it with "sudo /etc/cron.daily/automysqlbackup".  I took a look at /etc/crontab to see what command it's running, which is "test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )".  I switched to root (using the su command) and running "cd / && run-parts --report /etc/cron.daily" works, but running the full command doesn't.  It goes back to the prompt immediately, without any output.

Also, are there rules about the file names in /etc/cron.daily?  My file used to be called automysqlbackup.sh, I changed it to automysqlbackup today, so cron hasn't had a chance to attempt running it yet.

Any ideas?

---

### Post by geirha on 2009-02-16
> **nemesis256 said:**
> Last week I installed a new script to backup my database, and it doesn't seem to be running.  The script is [AutoMySQLBackup]("http://sourceforge.net/projects/automysqlbackup/"), and I put it in /etc/cron.daily with permissions as 0755.  

I can run it with "sudo /etc/cron.daily/automysqlbackup".  I took a look at /etc/crontab to see what command it's running, which is "test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )".  I switched to root (using the su command) and running "cd / && run-parts --report /etc/cron.daily" works, but running the full command doesn't.  It goes back to the prompt immediately, without any output.

Also, are there rules about the file names in /etc/cron.daily?  My file used to be called automysqlbackup.sh, I changed it to automysqlbackup today, so cron hasn't had a chance to attempt running it yet.

Any ideas?

It will not run scripts in /etc/cron.daily etc if they have an extension. Don't know why there would be such a limitation though. The cronjob, "test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )", first tests if the file /usr/sbin/anacron is executable. If it is executable, it does nothing. If it is not executable, it will instead run that run-parts command.

If anacron is executable (enabled), it will be run by cron from /etc/cron.d/anacron

Now, as for the script, running it like you did is not the same as running it from cron, because cron runs the script using /bin/sh (not /bin/bash) and has a much smaller environment set. Try starting a fresh /bin/sh shell as root, and see if it runs there:
```
$ env -i sudo sh
# cd /
# /etc/cron.daily/automysqlbackup

```

---

### Post by nemesis256 on 2009-02-16
My script has #!/bin/bash at the beginning of it.  Is that a problem?  Should I use #!/bin/sh instead?

I ran those 3 lines you posted and it worked fine like that.

---

### Post by geirha on 2009-02-16
No, if it's a bash script it should have /bin/bash on the hashbang. I don't see any apparent reason why it won't run. Does /var/log/syslog have any messages from anacron?
```
grep -i anacron /var/log/syslog
```

---

### Post by Phlee on 2009-02-16
I've ran into many instances where whitespaces kill me.  After every statement make sure their is a space and not tabs.  Probally won't help but it's a thought:p

---

### Post by bodhi.zazen on 2009-02-16
Not sure if this helps, but often errors in cron need you to specify the full path. cron runs in a limited environment so

/home/user/bin/script 

#or whatever you named your bash script and wherever it "lives"

rather then "script"

same with "test" or any other commands you run.

---

### Post by nemesis256 on 2009-02-17
So it turns out the period in the file name was causing the problem.  I have a backup file this morning.

---

