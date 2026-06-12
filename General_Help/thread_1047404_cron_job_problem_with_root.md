---
title: "cron job problem with root"
date: 2009-01-22
forum: General Help
---

### Post by esd2609 on 2009-01-22
Hi,

I recenlty locked my root account after reading up on how better to secure ssh access.  I enabled a root account after installing a lamp setup including webmin.  I did this based on a tutorial I read which now I see may not have been the right thing to do.

The problem I'm having is two cronjobs are no longer runing.  One is related to Webmin and the other has something to do with PHP.  I would like to run both jobs if at all possible.

I tried removing the jobs and then adding them again with a sudo command.  That didn't help.

Another set of question I have besides fixing this, is how can I tell based on the auth.log what cron job is trying to run.  I figured out which job I think it is based on the times it ran and the scheduled times in cron. I just want to make sure they're the jobs I think they are.  Also, why do other jobs run successfully as root and don't come up when I list the jobs with a crontab -l command?  I'm wondering if only the jobs that were added under the root account I enabled are the problem. 


Here's an example of the output from my auth.log:

> Jan 22 10:09:01 newubu CRON[11315]: pam_unix(cron:account): account root has expired (account expired)
Jan 22 10:17:01 newubu CRON[11504]: pam_unix(cron:account): account root has expired (account expired)
Jan 22 10:39:01 newubu CRON[11838]: pam_unix(cron:account): account root has expired (account expired)

Here's the output from sudo crontab -u root -l:

> 35 1 * * * /etc/webmin/cron/tempdelete.pl
9,39 * * * * [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm

Any help you can give me is much appreciated.

Thanks,

Tristan

---

### Post by cmnorton on 2009-01-22
Did you add these jobs by editing /etc/crontab directly or by crontab -e
running as root?

It sounds like you will need to find from which crontab these missing
commands are running. Start by looking in

/var/spool/cron/crontabs

Offhand, I do not know why you are getting the root account expired.

---

### Post by esd2609 on 2009-01-22
Thanks for the help.

I used the crontab -e way.  I checked the /var/spool/cron/crontabs and the jobs are there listed under the root directory.

I was doing some reading and it seems this may be a problem because I disabled the root account after enabling it.

---

### Post by esd2609 on 2009-01-22
I found out how to solve the problem.  I needed to set the root account so it didn't expire.  

I was able to do that with this command:

sudo chage -E-1 root

I think you can edit the shadow file as well.

Thanks for the help.  And thanks to this post: [http://www.teknynja.com/2008/09/obscure-ubuntu-tip-cron-user-account.html](http://www.teknynja.com/2008/09/obscure-ubuntu-tip-cron-user-account.html)

---

### Post by jrose78 on 2009-03-05
Wow I wish I had found this post before pulling my hair out trying to figure out why I could not run a rsnapshot cron file as root. I had done the same thing you did by enabling the root account and then locking it. I would have posted my problem but if you say you enabled a root account around here ... ahh well... lets just say I was afraid..   Thanks for the info and the link.

---

