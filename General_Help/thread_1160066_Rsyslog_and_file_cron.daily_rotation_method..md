---
title: "Rsyslog and file cron.daily rotation method."
date: 2009-05-15
forum: General Help
---

### Post by JPZG on 2009-05-15
Hello everyone,

Will try to keep this as short as possible, I decided to switch over to rsyslog and need a few pointers in the right direction to make the log rotation work.

Info:
-Running ubuntu 8.10
-Disabled sysklogd's autorun scripts and did my best at updating the cron.daily\sysklogd file.
-Rsyslog is running fine, using SQL data storage method.

My issue is that I'm unable to make the daily cron log rotation script made by Martin Schulze work with my newly made updates for Rsyslog. my linux experience is low btw.

locate rsyslog
```

locate rsyslog |more
/etc/rsyslog.conf
/etc/rsyslog.d
/etc/default/rsyslog
/etc/init.d/rsyslog
/etc/rc0.d/K20rsyslog
/etc/rc1.d/K20rsyslog
/etc/rc2.d/S20rsyslog
/etc/rc3.d/S20rsyslog
/etc/rc4.d/S20rsyslog
/etc/rc5.d/S20rsyslog
/etc/rc6.d/K20rsyslog
/usr/local/lib/rsyslog

```
/etc/cron.daily/sysklogd
```

test -x /usr/sbin/syslogd-listfiles || exit 0
#I disabled this and replaced it with the line below it.
#test -x /sbin/syslogd || exit 0
test -x /usr/local/lib/rsyslogd || exit 0
test -f /usr/share/sysklogd/dummy || exit 0

#Same here, disabled the old line, and added new one to reflect #rsyslog
#USER=$(ps -C syslogd -o user= | head -n 1)
USER=$(ps -C rsyslogd -o user= | head -n 1)
[ -z "${USER}" ] && USER="root" || true

set -e

cd /var/log

logs=$(syslogd-listfiles)

test -n "$logs" || exit 0

for LOG in $logs
do
   if [ -s $LOG ]; then
      savelog -g adm -m 640 -u ${USER} -c 7 $LOG >/dev/null
   fi
done

# Restart syslogd
#
# I changed this to reflect the new init script for rsyslog.
/etc/init.d/rsyslog restart > /dev/null

```

ps auwx |grep rsyslog
```

root     30836  0.0  1.0  54364  2336 ?        SNl  08:08   0:00 /usr/local/sbin/rsyslogd -c3 -f /etc/rsyslog.conf

```
I noticed that the script also works with /usr/sbin/syslogd-listfiles, but I didn't modify it. I noticed it checks the syslogd conf file, but since the same log files are being used, and rsyslog's conf file is different, I decided to not touch this.

The syslogd dummy file is also present. I've verified that sysklogd is not running. thus far I've noticed that only the syslog log file is being rotated. rsyslog is running as root.
cron.daily execution report doesn't seem to print out any errors regarding rsyslog log rotation.

I've looked around and haven't found anything that would help me update this cron script. Any tips would be greatly apreciated.

---

### Post by JPZG on 2009-05-18
Anyone ?  Any tips or ideas would be greatly appreciated.

---

### Post by JPZG on 2009-06-04
Anything anyone ? I'm going nuts with this. Any tips would be appreciated, I'm not expecting full support. I've tried changing the script so that it logs its output, but I just can't figure out why its not working. The best I've done thus far is to get the syslog log to rotate, but everything else remains the same.

---

