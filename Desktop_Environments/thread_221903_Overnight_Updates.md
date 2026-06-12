---
title: "Overnight Updates"
date: 2006-07-24
forum: Desktop Environments
---

### Post by firebadger on 2006-07-24
My ISP contract limits the amount of data I can download during the day but between midnight and 8am it is unlimited.  I'd like to configure the update manager to automatically download updates during this period.  Is this possible and if not, what is the best alternative approach?

Also, I have more than one computer running Ubuntu is it easy to get the other one (a laptop that is usually off) to download its updates from my desktop which is usually on.

Any advice much appreciated.

---

### Post by joselin on 2006-07-24
You can add a line in your cron with your apt-get commands (usually apt-get update & apt-get upgrade).

```
man crontab
```

Perhaps, you must need several parameters in your calls to apt-get.

```
apt-get -h
```

---

### Post by firebadger on 2006-07-24
I thought I might have to do it that way.  I was hoping there would be a way to do it with the update-manager app and I think that would be a nice enhancement - being able to schedule the checks and have it automatically download the files.

---

### Post by mvaniersel on 2006-07-24
It's possible to make the deb cache of one computer act as the repository source for the other. Here is some information I got from O'reilly's linux cookbook (haven't used it myself I must say):

```

apt-get install apt-proxy

```

then edit /etc/apt-proxy/apt-proxy.conf as needed. Point it to geographically close mirrors. Also you can safely lower the update frequency, by default it updates every 4 hours.

Look for man pages of apt-proxy and apt-proxy.conf

This works transparently. Whenever you request a deb that is not in the cache, it will get copied from the real repository. Otherwise, the cached deb is used, saving you some download time.

---

### Post by Johnathon on 2006-07-24
I had almost exactly the same query... look here :

[http://www.ubuntuforums.org/showthread.php?t=219915](http://www.ubuntuforums.org/showthread.php?t=219915)

---

### Post by firebadger on 2006-07-24
Thanks everybody - I'll have a bash at both the cron updates and the apt-proxy.

---

### Post by firebadger on 2006-08-05
Hi,

SLightly confused with cron behaviour...

I added a file called update to the directory /etc/cron.daily yesterday evening, but on checking the next morning, I couldn't find the log file in (/car/log/apt-updates) that would indicate it having run.  It then started running at 07.37am.  Any ideas as to why it ran at this time, given the contents of the config files as shown below. 

[FONT="Courier New"]
firebadger@pc1:/etc$ ls -l cron.daily
total 48
-rwxr-xr-x 1 root root  311 2005-05-03 03:10 0anacron
-rwxr-xr-x 1 root root 5566 2006-04-18 20:47 apt
-rwxr-xr-x 1 root root  314 2006-04-03 15:44 aptitude
-rwxr-xr-x 1 root root  502 2005-10-25 03:13 bsdmainutils
-rwxr-xr-x 1 root root  419 2006-03-20 06:25 find.notslocate
-rwxr-xr-x 1 root root   89 2005-10-25 11:32 logrotate
-rwxr-xr-x 1 root root  946 2005-09-26 16:12 man-db
-rwxr-xr-x 1 root root  189 2006-01-07 15:44 slocate
-rwxr-xr-x 1 root root 3227 2005-11-15 12:42 standard
-rwxr-xr-x 1 root root 1307 2006-04-24 19:36 sysklogd
-rwxr-xr-x 1 root root  204 2006-08-04 22:33 update
firebadger@pc1:/etc$ cat cron.daily/update
#! /bin/sh
echo "**************" >> /var/log/apt-updates
date >> /var/log/apt-updates
apt-get update >> /var/log/apt-updates
apt-get upgrade -y >> /var/log/apt-updates
echo "Updates installed (if found)"
firebadger@pc1:/etc$ cat crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#


firebadger@pc1:/etc$ cat anacrontab
# /etc/anacrontab: configuration file for anacron

# See anacron(8) and anacrontab(5) for details.

SHELL=/bin/sh
PATH=/sbin:/bin:/usr/sbin:/usr/bin

# These replace cron's entries
1       5       cron.daily       nice run-parts --report /etc/cron.daily
7       10      cron.weekly      nice run-parts --report /etc/cron.weekly
@monthly        15      cron.monthly nice run-parts --report /etc/cron.monthly


[/FONT]

---

### Post by firebadger on 2006-08-05
I am I right in thinking that the daily tasks should run at 6.25am - given my crontab file.  If so, does anybody have any idea why my script didn't run until 7.37am?

---

