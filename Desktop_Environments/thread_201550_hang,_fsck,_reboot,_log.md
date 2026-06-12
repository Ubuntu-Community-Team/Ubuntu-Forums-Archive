---
title: "hang, fsck, reboot, log?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by akutz on 2006-06-22
My Ubuntu Dapper Drake instanace hung on boot so I hard reset it.  Then it did an fsck (30-times w/o) and I saw some red text flash by as it finished with the fsck right before it rebooted again!  Is the data being written to tty9 being logged anywhere?  I tried adding:

console.info  /var/log/console.log

to my syslog.conf file but this did not seem to help.

I grepped /var/log for 'fsck' with no mention of it found.  I really want to know what fsck said right before it rebooted my box (perhaps my disks are going bad), and although it may be too late to find out for this time, I want to be able to know in the future.

Any help is appreciated.  Thanks!

---

