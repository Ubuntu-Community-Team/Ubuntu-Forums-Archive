---
title: "Cron compatibility Question"
date: 2006-08-16
forum: Desktop Environments
---

### Post by RobNY on 2006-08-16
I've installed Ubuntu 6 to replace an older Redhat 7 install.  U6 is fully updated.

Under RH, any cron jobs that ran from the root (or other) user's crontab automatically had the output of those jobs (stdout) emailed to the owner of the crontab.  I assumed this was a standard.

Under Ubuntu, this does not happen.  In fact, some of the longer-output cron jobs crashed with no warning or notice until I redirected the output to either /dev/null or to a file somewhere.

I have no email files in /var/mail.

My questions are:  

Is this the correct default behavior?  I read in the crontab man page that cron automatically emails the owner of the cronjob (or to the MAILTO env var).  

Is sendmail or postfix installed by default?  If I type "mail" in a terminal window, I get nothing...

What am I doing wrong? Do I need to install mail packages?

Thanks in advance,
Rob

---

### Post by RobNY on 2006-08-23
I realize now that this was not a smart question.  The answer is that mail is not installed by default.  Cron job output should be redirected appropriately. Hope this helps someone else.

---

