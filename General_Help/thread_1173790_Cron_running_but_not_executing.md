---
title: "Cron running but not executing"
date: 2009-05-30
forum: General Help
---

### Post by deeflex on 2009-05-30
Hi all!

I have been trying to set up a cron job for running my script every min.

I have used crontab -e to configure the cron, this is the output from crontab -l

```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
* * * * * /home/hajder/master_script

```

**Master_script**. I put the echo for debugging, it works when running the script directly in terminal, but not in cron :(.

```
echo "Script run" >> /home/hajder/script.log
php /var/www/sms.php &

```

**/var/log/syslog**

```
May 30 10:43:01 hajdeeer /USR/SBIN/CRON[18533]: (hajder) CMD (/home/hajder/master_script)
May 30 10:44:01 hajdeeer /USR/SBIN/CRON[18537]: (hajder) CMD (/home/hajder/master_script)
May 30 10:45:01 hajdeeer /USR/SBIN/CRON[18547]: (hajder) CMD (/home/hajder/master_script)

```

**/var/log/auth.log**

```
May 30 10:41:01 hajdeeer CRON[18523]: pam_unix(cron:session): session opened for user hajder by (uid=0)
May 30 10:42:01 hajdeeer CRON[18527]: pam_unix(cron:session): session opened for user hajder by (uid=0)
May 30 10:43:01 hajdeeer CRON[18532]: pam_unix(cron:session): session opened for user hajder by (uid=0)
etc....
```

Runs every minute at least. So I figure it's not directly cron, rather it's how the script is executed? The permissions are fine...so I got no clue what could be wrong now :(.

---

### Post by kpkeerthi on 2009-05-30
> **deeflex said:**
> 
```
echo "Script run" >> /home/hajder/script.log
[COLOR="Red"]php [/COLOR]/var/www/sms.php[COLOR="Red"][COLOR="RoyalBlue"] >> /home/hajder/script.log [/COLOR][/COLOR][COLOR="SeaGreen"]&[/COLOR]

```


Executables, when referred within crontab, should be referred using absolute path. Change [COLOR="Red"]php[/COLOR] to the full path that the below command prints
```
which php
```

The blues one will send the output of your php command to the log file so you can investigate later what was the outcome. And the trailing[COLOR="SeaGreen"] &[/COLOR] is not required when run from cron.

---

### Post by deeflex on 2009-05-30
Ok thanks alot for the fast reply. 

Now it works!!!:):popcorn:

---

