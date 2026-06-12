---
title: "system log restarting"
date: 2009-06-13
forum: General Help
---

### Post by mitjab on 2009-06-13
I get every day 100 messages that system log restaring and computer start working very slow. I now that restarting log everyday is normal but not 100 times ...


This is some part of nano /var/log/system

```

Jun 13 07:02:22 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:02:22 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:02:37 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:02:37 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:02:52 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:02:52 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:03:07 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:03:07 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:03:22 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:03:22 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:03:37 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:03:37 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:03:52 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:03:52 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:04:07 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:04:07 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:04:22 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:04:22 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:04:37 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:04:37 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:04:52 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:04:52 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:05:02 server /USR/SBIN/CRON[9092]: (mitjab) CMD (/home/mitjab/BOTI/scream/pisg/pisg --silent)
Jun 13 07:05:07 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:05:07 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:05:13 server sendmail[9087]: n5D550aN009087: from=logcheck, size=679, class=0, nrcpts=1, msgid=<200906130505.n5D550aN009087@mitjab.homelinux.net>, relay=logcheck@localhost
Jun 13 07:05:14 server sendmail[9087]: n5D550aN009087: to=logcheck, delay=00:00:06, mailer=relay, pri=30679, stat=queued
Jun 13 07:05:22 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:05:22 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:05:37 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:05:37 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:05:52 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:05:52 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:06:07 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:06:07 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:06:22 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:06:22 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:06:22 server sm-mta[5514]: runqueue: Skipping queue run -- load average too high
Jun 13 07:06:37 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:06:37 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:06:52 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:06:52 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:07:07 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:07:07 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:07:22 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:07:22 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:07:37 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:07:37 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:07:52 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:07:52 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41
Jun 13 07:08:07 server sm-mta[5514]: rejecting connections on daemon MTA-v4: load average: 41
Jun 13 07:08:07 server sm-mta[5514]: rejecting connections on daemon MSP-v4: load average: 41


```

---

### Post by mitjab on 2009-06-14
any idea why this happens? When system restarting log system works so slow that i can not ssh remote or do anything. Only resatrt helps...

Please help me.

Thx

---

### Post by mitjab on 2009-06-14
[email]mitjab@server:/etc/cron.daily[/email]$ ls
apache2  apt  aptitude  bsdmainutils  logrotate  man-db  mlocate  netkit-inetd  ntp  quota  samba  sendmail  standard  sysklogd


this is my cron.daily if helps

---

