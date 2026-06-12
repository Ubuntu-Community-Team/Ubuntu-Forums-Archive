---
title: "Sysklogd issue"
date: 2006-01-03
forum: General Help
---

### Post by z84976 on 2006-01-03
I hope I've got this in the right section.  I've been using Linux since the first Slackware release waaay long ago, but only moved to ubuntu within the last year.  I never was a Debian user (slack, suse, gentoo only) so maybe I missed a bus or something, but this Ubuntu bug has me, both as my primary desktop (breezy) and my server.

Anyway, I'm using Hoary as a web/mail server and thus like to occasionally  view my system logs.  Everything is being logged just fine, with one HUGE problem that REALLY makes troubleshooting a pain:  no log files are updated during the day.  Every day at 7am they are all updated and all the data from the day before shows up in there, but NOTHING during the day.  I thought maybe telling syslog to sync writes would help... nope.  I can't find anything anywhere.  Am I insane?  I can't use tail -f /var/log/mail.log to see what's up with Spamassassin after a tweak, for example, because it won't be changing until tomorrow.  I'm desperate and feel really pretty damned silly because I don't just "know" how to fixt this.

syslog.conf (comments removed):

auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          /var/log/syslog
#cron.*                         /var/log/cron.log
daemon.*                        -/var/log/daemon.log
kern.*                          /var/log/kern.log
lpr.*                           /var/log/lpr.log
mail.*                          /var/log/mail.log
user.*                          /var/log/user.log
uucp.*                          /var/log/uucp.log

mail.info                       /var/log/mail.info
mail.warn                       /var/log/mail.warn
mail.err                        /var/log/mail.err

news.crit                       /var/log/news/news.crit
news.err                        /var/log/news/news.err
news.notice                     -/var/log/news/news.notice

*.=debug;\
        auth,authpriv.none;\
        news.none;mail.none     -/var/log/debug
*.=info;*.=notice;*.=warn;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none          /var/log/messages

*.emerg                         *

daemon.*;mail.*;\
        news.crit;news.err;news.notice;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       |/dev/xconsole

kern.=debug     /var/log/bandwidth


snippet from ls -la /var/log:
-rw-r-----   1 root   adm      229295 2006-01-03 07:00 mail.log
-rw-r-----   1 root   adm      618585 2006-01-01 06:47 mail.log.0
-rw-r-----   1 root   adm       40746 2005-12-25 06:47 mail.log.1.gz
-rw-r-----   1 root   adm       48027 2005-12-18 06:46 mail.log.2.gz
-rw-r-----   1 root   adm       35197 2005-12-11 06:47 mail.log.3.gz

Basically none of the logfiles have dates more recent than about 7am today.  tomorrow, it'll be the same story.  Can anybody point me to what I'm obviously missing here?     :confused:

---

