---
title: "awstats and cron"
date: 2006-09-13
forum: Desktop Environments
---

### Post by mitjab on 2006-09-13
```
Automatising the stats generation using Cron:
If we check the file installed by awstats and search for the word cron using the following command line:

~:$dpkg -L awstats | grep cron
/etc/cron.d
/etc/cron.d/awstats

we can see that awstats already installed a cron job which contain:

0,10,20,30,40,50 * * * * www-data [ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=awstats -update >/dev/null

which basically check every 10 minutes that file /usr/lib/cgi-bin/awstats.pl is executable AND file /etc/awstats/awstats.conf exists and is a regular file AND file /var/log/apache/access.log is readable, if this is TRUE, it executes awstats.pl with the config awstats.

As the file /etc/awstats/awstats.awstats.conf does not exist, it will take /etc/awstats/awstats.conf by default.
What we can do in the first, is to use that file for our needs. Let say I want update my stats every day at 2am, I will change the line to:

0 2 * * * * www-data [ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=mysite.com -update >/dev/null
 
```

but doesn't update every 10 minutes

i must enter manually
```
sudo -u www-data /usr/bin/perl /usr/lib/cgi-bin/awstats.pl -update -config=www.mysite.org
```

that awstats site is updated.

Why cron not update it automatically?

Thx

---

