---
title: "Ubuntu Bluescreen"
date: 2008-12-18
forum: General Help
---

### Post by pt.linux on 2008-12-18
Hi!

I have ubuntu since last week and after i run it like 30 min I have a bluescreen!!!
What should I do???

---

### Post by Izek on 2008-12-18
Uh, what does the blue screen say?

Is it this: [http://img134.imageshack.us/img134/8596/3800yq1.jpg](http://img134.imageshack.us/img134/8596/3800yq1.jpg)

---

### Post by pt.linux on 2008-12-18
I can't take any print screen couse the system blocks

---

### Post by Izek on 2008-12-18
> **pt.linux said:**
> I can't take any print screen couse the system blocks

> **Titan8990 said:**
> Post the results of the following commands:

dmesg

cat /var/log/syslog
cat /var/log/syslog.0

if you can

---

### Post by pt.linux on 2008-12-18
I think that is "Writing cache out of request time" but I'm not sure if it's was that

---

### Post by pt.linux on 2008-12-18
> 
$ cat /var/log/syslog
Dec 18 08:58:33 espLPT08 syslogd 1.5.0#2ubuntu6: restart.
Dec 18 08:58:33 espLPT08 anacron[5559]: Job `cron.daily' terminated
Dec 18 08:58:33 espLPT08 anacron[5559]: Normal exit (1 job run)
Dec 18 09:06:17 espLPT08 /usr/lib/vmware/bin/vmware-hostd[6244]: Accepted password for user itadmin from 127.0.0.1
Dec 18 09:06:56 espLPT08 kernel: [ 2768.128909] /dev/vmmon[8167]: PTSC: initialized at 2000000000 Hz using reference clock
Dec 18 09:06:58 espLPT08 kernel: [ 2769.817012] /dev/vmnet: open called by PID 8172 (vmware-vmx)
Dec 18 09:06:58 espLPT08 kernel: [ 2769.817047] device eth1 entered promiscuous mode
Dec 18 09:06:58 espLPT08 kernel: [ 2769.817102] bridge-eth1: enabled promiscuous mode
Dec 18 09:06:58 espLPT08 kernel: [ 2769.817104] /dev/vmnet: port on hub 0 successfully opened
Dec 18 09:07:51 espLPT08 kernel: [ 2823.298118] device eth1 left promiscuous mode
Dec 18 09:07:51 espLPT08 kernel: [ 2823.298211] bridge-eth1: disabled promiscuous mode
Dec 18 09:07:51 espLPT08 kernel: [ 2823.301511] /dev/vmnet: open called by PID 8172 (vmware-vmx)
Dec 18 09:07:51 espLPT08 kernel: [ 2823.303605] device eth1 entered promiscuous mode
Dec 18 09:07:51 espLPT08 kernel: [ 2823.303669] bridge-eth1: enabled promiscuous mode
Dec 18 09:07:51 espLPT08 kernel: [ 2823.303676] /dev/vmnet: port on hub 0 successfully opened
Dec 18 09:09:01 espLPT08 /USR/SBIN/CRON[8728]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 18 09:10:52 espLPT08 kernel: [ 3004.294606] type=1505 audit(1229587852.736:5): operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=10712
Dec 18 09:10:53 espLPT08 kernel: [ 3005.001802] type=1505 audit(1229587853.444:6): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=10717
Dec 18 09:10:53 espLPT08 kernel: [ 3005.008391] type=1505 audit(1229587853.452:7): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=10717
Dec 18 09:17:01 espLPT08 /USR/SBIN/CRON[10940]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 18 09:39:02 espLPT08 /USR/SBIN/CRON[11469]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 18 10:01:09 espLPT08 -- MARK --
Dec 18 10:09:01 espLPT08 /USR/SBIN/CRON[11553]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 18 10:17:01 espLPT08 /USR/SBIN/CRON[11635]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 18 10:39:01 espLPT08 /USR/SBIN/CRON[12230]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 18 11:01:09 espLPT08 -- MARK --
Dec 18 11:09:02 espLPT08 /USR/SBIN/CRON[14041]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 18 11:17:01 espLPT08 /USR/SBIN/CRON[14108]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 18 11:39:01 espLPT08 /USR/SBIN/CRON[14206]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 18 12:01:09 espLPT08 -- MARK --
Dec 18 12:09:01 espLPT08 /USR/SBIN/CRON[14878]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 18 12:17:01 espLPT08 /USR/SBIN/CRON[14950]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 18 12:39:01 espLPT08 /USR/SBIN/CRON[15017]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 18 13:01:09 espLPT08 -- MARK --
Dec 18 13:09:01 espLPT08 /USR/SBIN/CRON[16220]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)


The other one is to big to be posted

---

### Post by Izek on 2008-12-18
> **pt.linux said:**
> The other one is to big to be posted

Use [http://www.paste.org/](http://www.paste.org/)

---

### Post by pt.linux on 2008-12-18
but is to big to copy
I can't select it all

---

### Post by Izek on 2008-12-18
What's the output of

free -m

in terminal?

---

### Post by pt.linux on 2008-12-18
free -m
             total       used       free     shared    buffers     cached
Mem:          1882       1854         28          0         18        978
-/+ buffers/cache:        857       1024
Swap:         5514        215       5299

---

### Post by any.linux12 on 2008-12-18
Maybe it was a bad installation!
You should try to reinstall and then see if is a defect on the installation or a hardware defect

---

### Post by pt.linux on 2008-12-19
I have a new installationand now it's ok. Thanks but I would like to know what was the problem

---

