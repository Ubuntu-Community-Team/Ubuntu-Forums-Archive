---
title: "&quot;sigfile not found&quot; error by cron"
date: 2009-01-04
forum: General Help
---

### Post by donpaolo on 2009-01-04
My ubuntu intrepid keeps on all the day long.

My crontab is:

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
10 1	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 1	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 1	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

However, every time cron is activated, I get a line like this in syslog:

Jan  4 10:17:01 paolo CRON[26282]: Sigfile not found
Jan  4 10:17:01 paolo /USR/SBIN/CRON[26288]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  4 10:17:01 paolo CRON[26282]: Sigfile not found

or 

Jan  4 18:00:01 paolo CRON[13594]: Sigfile not found
Jan  4 18:00:01 paolo /USR/SBIN/CRON[13601]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 18:00:02 paolo CRON[13594]: Sigfile not found

Besides that, every time I begin working with the pc in the morning I see my cpu and hd heavily loaded, and that's due to the programs in cron.daily, expecially updatedb and apt-cacher-cleanup. It seems like cron is able to execute them only when I'm working with the computer.

Here is my syslog from the midnight to 8 a.m.

Jan  4 00:00:01 paolo CRON[27981]: Sigfile not found
Jan  4 00:00:01 paolo /USR/SBIN/CRON[27987]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 00:00:02 paolo CRON[27981]: Sigfile not found
Jan  4 00:02:21 paolo ntpd[4950]: kernel time sync status change 0001
Jan  4 00:09:01 paolo CRON[5481]: Sigfile not found
Jan  4 00:09:01 paolo /USR/SBIN/CRON[5487]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 00:09:01 paolo CRON[5481]: Sigfile not found
Jan  4 00:10:01 paolo CRON[6665]: Sigfile not found
Jan  4 00:10:01 paolo /USR/SBIN/CRON[6674]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 00:10:02 paolo CRON[6665]: Sigfile not found
Jan  4 00:17:01 paolo CRON[14340]: Sigfile not found
Jan  4 00:17:01 paolo /USR/SBIN/CRON[14346]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  4 00:17:01 paolo CRON[14340]: Sigfile not found
Jan  4 00:20:01 paolo CRON[17582]: Sigfile not found
Jan  4 00:20:01 paolo /USR/SBIN/CRON[17588]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 00:20:03 paolo CRON[17582]: Sigfile not found
Jan  4 00:30:01 paolo CRON[28470]: Sigfile not found
Jan  4 00:30:01 paolo /USR/SBIN/CRON[28476]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 00:30:02 paolo CRON[28470]: Sigfile not found
Jan  4 00:39:01 paolo CRON[5975]: Sigfile not found
Jan  4 00:39:01 paolo /USR/SBIN/CRON[5981]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 00:39:01 paolo CRON[5975]: Sigfile not found
Jan  4 00:40:01 paolo CRON[7163]: Sigfile not found
Jan  4 00:40:01 paolo /USR/SBIN/CRON[7169]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 00:40:02 paolo CRON[7163]: Sigfile not found
Jan  4 00:50:01 paolo CRON[18063]: Sigfile not found
Jan  4 00:50:01 paolo /USR/SBIN/CRON[18069]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 00:50:02 paolo CRON[18063]: Sigfile not found
Jan  4 01:00:01 paolo CRON[28960]: Sigfile not found
Jan  4 01:00:01 paolo /USR/SBIN/CRON[28966]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 01:00:02 paolo CRON[28960]: Sigfile not found
Jan  4 01:09:01 paolo CRON[6487]: Sigfile not found
Jan  4 01:09:01 paolo /USR/SBIN/CRON[6493]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 01:09:01 paolo CRON[6487]: Sigfile not found
Jan  4 01:10:01 paolo CRON[7660]: Sigfile not found
Jan  4 01:10:01 paolo CRON[7665]: Sigfile not found
Jan  4 01:10:01 paolo /USR/SBIN/CRON[7667]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Jan  4 01:10:01 paolo CRON[7660]: Sigfile not found
Jan  4 01:10:01 paolo /USR/SBIN/CRON[7673]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 01:10:02 paolo CRON[7665]: Sigfile not found
Jan  4 01:17:01 paolo CRON[15354]: Sigfile not found
Jan  4 01:17:01 paolo /USR/SBIN/CRON[15360]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  4 01:17:01 paolo CRON[15354]: Sigfile not found
Jan  4 01:20:01 paolo CRON[18593]: Sigfile not found
Jan  4 01:20:01 paolo /USR/SBIN/CRON[18599]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 01:20:02 paolo CRON[18593]: Sigfile not found
Jan  4 01:30:01 paolo CRON[29484]: Sigfile not found
Jan  4 01:30:01 paolo /USR/SBIN/CRON[29490]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 01:30:02 paolo CRON[29484]: Sigfile not found
Jan  4 01:39:01 paolo CRON[7029]: Sigfile not found
Jan  4 01:39:01 paolo /USR/SBIN/CRON[7035]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 01:39:01 paolo CRON[7029]: Sigfile not found
Jan  4 01:40:01 paolo CRON[8179]: Sigfile not found
Jan  4 01:40:01 paolo /USR/SBIN/CRON[8185]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 01:40:02 paolo CRON[8179]: Sigfile not found
Jan  4 01:44:48 paolo ntpd[4950]: kernel time sync status change 4001
Jan  4 01:47:01 paolo CRON[15859]: Sigfile not found
Jan  4 01:47:01 paolo /USR/SBIN/CRON[15865]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly ))
Jan  4 01:47:01 paolo CRON[15859]: Sigfile not found
Jan  4 01:50:01 paolo CRON[19099]: Sigfile not found
Jan  4 01:50:01 paolo /USR/SBIN/CRON[19105]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 01:50:02 paolo CRON[19099]: Sigfile not found
Jan  4 01:51:27 paolo ntpd[4950]: synchronized to 193.79.237.14, stratum 1
Jan  4 01:51:27 paolo ntpd[4950]: kernel time sync status change 0001
Jan  4 02:00:01 paolo CRON[29991]: Sigfile not found
Jan  4 02:00:01 paolo /USR/SBIN/CRON[29997]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 02:00:02 paolo CRON[29991]: Sigfile not found
Jan  4 02:08:33 paolo ntpd[4950]: synchronized to 130.149.17.21, stratum 1
Jan  4 02:09:01 paolo CRON[7565]: Sigfile not found
Jan  4 02:09:01 paolo /USR/SBIN/CRON[7571]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 02:09:01 paolo CRON[7565]: Sigfile not found
Jan  4 02:10:01 paolo CRON[8712]: Sigfile not found
Jan  4 02:10:01 paolo /USR/SBIN/CRON[8718]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 02:10:02 paolo CRON[8712]: Sigfile not found
Jan  4 02:17:01 paolo CRON[16363]: Sigfile not found
Jan  4 02:17:01 paolo /USR/SBIN/CRON[16369]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  4 02:17:01 paolo CRON[16363]: Sigfile not found
Jan  4 02:20:01 paolo CRON[19668]: Sigfile not found
Jan  4 02:20:02 paolo /USR/SBIN/CRON[19674]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 02:20:02 paolo CRON[19668]: Sigfile not found
Jan  4 02:30:02 paolo CRON[30554]: Sigfile not found
Jan  4 02:30:02 paolo /USR/SBIN/CRON[30561]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 02:30:02 paolo CRON[30554]: Sigfile not found
Jan  4 02:39:01 paolo CRON[8116]: Sigfile not found
Jan  4 02:39:02 paolo /USR/SBIN/CRON[8123]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 02:39:02 paolo CRON[8116]: Sigfile not found
Jan  4 02:40:01 paolo CRON[9235]: Sigfile not found
Jan  4 02:40:01 paolo /USR/SBIN/CRON[9241]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 02:40:02 paolo CRON[9235]: Sigfile not found
Jan  4 02:50:01 paolo CRON[20137]: Sigfile not found
Jan  4 02:50:01 paolo /USR/SBIN/CRON[20143]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 02:50:02 paolo CRON[20137]: Sigfile not found
Jan  4 03:00:01 paolo CRON[31042]: Sigfile not found
Jan  4 03:00:01 paolo /USR/SBIN/CRON[31048]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 03:00:02 paolo CRON[31042]: Sigfile not found
Jan  4 03:00:12 paolo ntpd[4950]: synchronized to 130.149.17.8, stratum 1
Jan  4 03:09:01 paolo CRON[8596]: Sigfile not found
Jan  4 03:09:01 paolo /USR/SBIN/CRON[8605]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 03:09:01 paolo CRON[8596]: Sigfile not found
Jan  4 03:10:01 paolo CRON[9729]: Sigfile not found
Jan  4 03:10:01 paolo /USR/SBIN/CRON[9735]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 03:10:02 paolo CRON[9729]: Sigfile not found
Jan  4 03:17:01 paolo CRON[17399]: Sigfile not found
Jan  4 03:17:01 paolo /USR/SBIN/CRON[17405]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  4 03:17:01 paolo CRON[17399]: Sigfile not found
Jan  4 03:20:01 paolo CRON[20689]: Sigfile not found
Jan  4 03:20:01 paolo /USR/SBIN/CRON[20695]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 03:20:02 paolo CRON[20689]: Sigfile not found
Jan  4 03:30:01 paolo CRON[31615]: Sigfile not found
Jan  4 03:30:01 paolo /USR/SBIN/CRON[31621]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 03:30:02 paolo CRON[31615]: Sigfile not found
Jan  4 03:32:29 paolo ntpd[4950]: synchronized to 193.79.237.14, stratum 1
Jan  4 03:39:01 paolo CRON[9173]: Sigfile not found
Jan  4 03:39:01 paolo /USR/SBIN/CRON[9179]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 03:39:01 paolo CRON[9173]: Sigfile not found
Jan  4 03:40:01 paolo CRON[10308]: Sigfile not found
Jan  4 03:40:01 paolo /USR/SBIN/CRON[10314]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 03:40:02 paolo CRON[10308]: Sigfile not found
Jan  4 03:50:01 paolo CRON[21220]: Sigfile not found
Jan  4 03:50:01 paolo /USR/SBIN/CRON[21226]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 03:50:02 paolo CRON[21220]: Sigfile not found
Jan  4 04:00:01 paolo CRON[32128]: Sigfile not found
Jan  4 04:00:01 paolo /USR/SBIN/CRON[32134]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 04:00:02 paolo CRON[32128]: Sigfile not found
Jan  4 04:09:01 paolo CRON[9685]: Sigfile not found
Jan  4 04:09:01 paolo /USR/SBIN/CRON[9691]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 04:09:01 paolo CRON[9685]: Sigfile not found
Jan  4 04:10:01 paolo CRON[10817]: Sigfile not found
Jan  4 04:10:01 paolo /USR/SBIN/CRON[10823]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 04:10:02 paolo CRON[10817]: Sigfile not found
Jan  4 04:17:01 paolo CRON[18487]: Sigfile not found
Jan  4 04:17:01 paolo /USR/SBIN/CRON[18493]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  4 04:17:01 paolo CRON[18487]: Sigfile not found
Jan  4 04:20:01 paolo CRON[21792]: Sigfile not found
Jan  4 04:20:01 paolo /USR/SBIN/CRON[21799]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 04:20:02 paolo CRON[21792]: Sigfile not found
Jan  4 04:30:01 paolo CRON[32714]: Sigfile not found
Jan  4 04:30:01 paolo /USR/SBIN/CRON[32720]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 04:30:02 paolo CRON[32714]: Sigfile not found
Jan  4 04:39:01 paolo CRON[10267]: Sigfile not found
Jan  4 04:39:01 paolo /USR/SBIN/CRON[10273]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 04:39:01 paolo CRON[10267]: Sigfile not found
Jan  4 04:40:01 paolo CRON[11403]: Sigfile not found
Jan  4 04:40:01 paolo /USR/SBIN/CRON[11409]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 04:40:02 paolo CRON[11403]: Sigfile not found
Jan  4 04:50:01 paolo CRON[22322]: Sigfile not found
Jan  4 04:50:01 paolo /USR/SBIN/CRON[22337]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 04:50:02 paolo CRON[22322]: Sigfile not found
Jan  4 04:57:51 paolo ntpd[4950]: kernel time sync status change 4001
Jan  4 04:59:47 paolo ntpd[4950]: synchronized to 130.149.17.8, stratum 1
Jan  4 04:59:47 paolo ntpd[4950]: kernel time sync status change 0001
Jan  4 05:00:01 paolo CRON[769]: Sigfile not found
Jan  4 05:00:01 paolo /USR/SBIN/CRON[775]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 05:00:02 paolo CRON[769]: Sigfile not found
Jan  4 05:09:01 paolo CRON[10787]: Sigfile not found
Jan  4 05:09:01 paolo /USR/SBIN/CRON[10793]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 05:09:01 paolo CRON[10787]: Sigfile not found
Jan  4 05:10:01 paolo CRON[11931]: Sigfile not found
Jan  4 05:10:01 paolo /USR/SBIN/CRON[11937]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 05:10:02 paolo CRON[11931]: Sigfile not found
Jan  4 05:17:01 paolo CRON[19618]: Sigfile not found
Jan  4 05:17:01 paolo /USR/SBIN/CRON[19624]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  4 05:17:01 paolo CRON[19618]: Sigfile not found
Jan  4 05:20:01 paolo CRON[22869]: Sigfile not found
Jan  4 05:20:02 paolo /USR/SBIN/CRON[22887]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 05:20:04 paolo CRON[22869]: Sigfile not found
Jan  4 05:30:01 paolo CRON[1333]: Sigfile not found
Jan  4 05:30:01 paolo /USR/SBIN/CRON[1339]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 05:30:02 paolo CRON[1333]: Sigfile not found
Jan  4 05:32:50 paolo ntpd[4950]: synchronized to 193.79.237.14, stratum 1
Jan  4 05:39:01 paolo CRON[11333]: Sigfile not found
Jan  4 05:39:01 paolo /USR/SBIN/CRON[11339]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 05:39:01 paolo CRON[11333]: Sigfile not found
Jan  4 05:40:01 paolo CRON[12493]: Sigfile not found
Jan  4 05:40:01 paolo /USR/SBIN/CRON[12499]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 05:40:02 paolo CRON[12493]: Sigfile not found
Jan  4 05:50:01 paolo CRON[23413]: Sigfile not found
Jan  4 05:50:01 paolo /USR/SBIN/CRON[23419]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 05:50:02 paolo CRON[23413]: Sigfile not found
Jan  4 06:00:01 paolo CRON[1855]: Sigfile not found
Jan  4 06:00:01 paolo /USR/SBIN/CRON[1861]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 06:00:02 paolo CRON[1855]: Sigfile not found
Jan  4 06:06:11 paolo ntpd[4950]: synchronized to 193.67.79.202, stratum 1
Jan  4 06:09:01 paolo CRON[11883]: Sigfile not found
Jan  4 06:09:01 paolo /USR/SBIN/CRON[11889]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 06:09:01 paolo CRON[11883]: Sigfile not found
Jan  4 06:10:01 paolo CRON[13032]: Sigfile not found
Jan  4 06:10:01 paolo /USR/SBIN/CRON[13038]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 06:10:02 paolo CRON[13032]: Sigfile not found
Jan  4 06:17:01 paolo CRON[20696]: Sigfile not found
Jan  4 06:17:01 paolo /USR/SBIN/CRON[20702]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  4 06:17:01 paolo CRON[20696]: Sigfile not found
Jan  4 06:20:01 paolo CRON[23995]: Sigfile not found
Jan  4 06:20:01 paolo /USR/SBIN/CRON[24001]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 06:20:02 paolo CRON[23995]: Sigfile not found
Jan  4 06:30:01 paolo CRON[2476]: Sigfile not found
Jan  4 06:30:01 paolo /USR/SBIN/CRON[2482]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 06:30:02 paolo CRON[2476]: Sigfile not found
Jan  4 06:39:01 paolo CRON[12488]: Sigfile not found
Jan  4 06:39:01 paolo /USR/SBIN/CRON[12495]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 06:39:01 paolo CRON[12488]: Sigfile not found
Jan  4 06:40:01 paolo CRON[13640]: Sigfile not found
Jan  4 06:40:01 paolo /USR/SBIN/CRON[13646]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 06:40:02 paolo CRON[13640]: Sigfile not found
Jan  4 06:42:12 paolo ntpd[4950]: synchronized to 193.79.237.14, stratum 1
Jan  4 06:50:01 paolo CRON[24542]: Sigfile not found
Jan  4 06:50:01 paolo /USR/SBIN/CRON[24548]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 06:50:02 paolo CRON[24542]: Sigfile not found
Jan  4 07:00:01 paolo CRON[3003]: Sigfile not found
Jan  4 07:00:01 paolo /USR/SBIN/CRON[3009]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 07:00:02 paolo CRON[3003]: Sigfile not found
Jan  4 07:09:01 paolo CRON[13029]: Sigfile not found
Jan  4 07:09:01 paolo /USR/SBIN/CRON[13035]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 07:09:01 paolo CRON[13029]: Sigfile not found
Jan  4 07:10:01 paolo CRON[14179]: Sigfile not found
Jan  4 07:10:01 paolo /USR/SBIN/CRON[14185]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 07:10:02 paolo CRON[14179]: Sigfile not found
Jan  4 07:17:01 paolo CRON[21827]: Sigfile not found
Jan  4 07:17:01 paolo /USR/SBIN/CRON[21841]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  4 07:17:01 paolo CRON[21827]: Sigfile not found
Jan  4 07:20:01 paolo CRON[25136]: Sigfile not found
Jan  4 07:20:01 paolo /USR/SBIN/CRON[25142]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 07:20:02 paolo CRON[25136]: Sigfile not found
Jan  4 07:30:01 paolo CRON[3594]: Sigfile not found
Jan  4 07:30:01 paolo CRON[3599]: Sigfile not found
Jan  4 07:30:01 paolo /USR/SBIN/CRON[3601]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Jan  4 07:30:01 paolo /USR/SBIN/CRON[3608]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 07:30:02 paolo anacron[3687]: Anacron 2.3 started on 2009-01-04
Jan  4 07:30:02 paolo CRON[3594]: Sigfile not found
Jan  4 07:30:02 paolo anacron[3687]: Will run job `cron.daily' in 5 min.
Jan  4 07:30:02 paolo anacron[3687]: Jobs will be executed sequentially
Jan  4 07:30:03 paolo CRON[3599]: Sigfile not found
Jan  4 07:33:30 paolo ntpd[4950]: synchronized to 130.149.17.21, stratum 1
Jan  4 07:35:02 paolo anacron[3687]: Job `cron.daily' started
Jan  4 07:35:02 paolo anacron[9360]: Updated timestamp for job `cron.daily' to 2009-01-04
Jan  4 07:39:08 paolo CRON[14163]: Sigfile not found
Jan  4 07:39:08 paolo /USR/SBIN/CRON[14170]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Jan  4 07:39:21 paolo CRON[14163]: Sigfile not found
Jan  4 07:39:21 paolo NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Jan  4 07:40:08 paolo CRON[15286]: Sigfile not found
Jan  4 07:40:08 paolo /USR/SBIN/CRON[15292]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 07:40:20 paolo CRON[15286]: Sigfile not found
Jan  4 07:50:02 paolo CRON[26044]: Sigfile not found
Jan  4 07:50:02 paolo /USR/SBIN/CRON[26072]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jan  4 07:50:12 paolo CRON[26044]: Sigfile not found


Any clue?

---

### Post by domu on 2009-01-15
see [https://bugs.launchpad.net/ecryptfs/+bug/293434:](https://bugs.launchpad.net/ecryptfs/+bug/293434:)
> pam_ecryptfs: "Sigfile not found" messages are not necessary.

If the root user does not have an encrypted private directory set up, and has cronjobs, /var/log/syslog can get ***very*** noisy.

So this is a bug, but not a serious one. Like me, you have ecryptfs installed, but not enabled for the root user. 

If you don't really want ecryptfs then follow the instructions at [https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup](https://help.ubuntu.com/community/EncryptedPrivateDirectory#How%20to%20Remove%20an%20Encrypted%20Private%20Directory%20Setup) to remove it. You need to remove the folders for each user who has them, then uninstall ecryptfs as shown. This will stop the messages.

---

