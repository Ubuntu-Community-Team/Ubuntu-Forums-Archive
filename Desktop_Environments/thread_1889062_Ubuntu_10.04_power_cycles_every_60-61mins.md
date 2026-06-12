---
title: "Ubuntu 10.04 power cycles every 60-61mins"
date: 2011-11-30
forum: Desktop Environments
---

### Post by brianmrowe on 2011-11-30
Yesterday my machine started power cycling every 60 to 61 mins.

root@saturn:/etc/cron.d# last reboot
reboot   system boot  2.6.32-35-generi Wed Nov 30 14:02 - 14:32  (00:29)    
reboot   system boot  2.6.32-35-generi Wed Nov 30 13:02 - 14:32  (01:29)    
reboot   system boot  2.6.32-35-generi Wed Nov 30 12:02 - 14:32  (02:30)    
reboot   system boot  2.6.32-35-generi Wed Nov 30 11:02 - 14:32  (03:30)    
reboot   system boot  2.6.32-35-generi Wed Nov 30 10:01 - 14:32  (04:30)    
reboot   system boot  2.6.32-35-generi Wed Nov 30 09:01 - 14:32  (05:30)    
reboot   system boot  2.6.32-35-generi Wed Nov 30 08:01 - 14:32  (06:31)    
reboot   system boot  2.6.32-35-generi Wed Nov 30 07:00 - 14:32  (07:31)    
reboot   system boot  2.6.32-35-generi Wed Nov 30 06:00 - 14:32  (08:31)    
reboot   system boot  2.6.32-35-generi Wed Nov 30 05:00 - 14:32  (09:32)    
reboot   system boot  2.6.32-35-generi Wed Nov 30 04:00 - 14:32  (10:32)    
reboot   system boot  2.6.32-35-generi Wed Nov 30 02:59 - 14:32  (11:32)    
reboot   system boot  2.6.32-35-generi Wed Nov 30 01:59 - 14:32  (12:32)    
reboot   system boot  2.6.32-35-generi Wed Nov 30 00:59 - 14:32  (13:33)    
reboot   system boot  2.6.32-35-generi Tue Nov 29 23:58 - 14:32  (14:33)    
reboot   system boot  2.6.32-35-generi Tue Nov 29 22:59 - 14:32  (15:33)    
reboot   system boot  2.6.32-35-generi Tue Nov 29 21:58 - 14:32  (16:34)    
reboot   system boot  2.6.32-35-generi Tue Nov 29 20:58 - 14:32  (17:34)    
reboot   system boot  2.6.32-35-generi Tue Nov 29 19:57 - 14:32  (18:34)    
reboot   system boot  2.6.32-35-generi Tue Nov 29 18:57 - 14:32  (19:34)    
reboot   system boot  2.6.32-35-generi Tue Nov 29 17:57 - 14:32  (20:35)    
reboot   system boot  2.6.32-35-generi Tue Nov 29 16:57 - 14:32  (21:35) 

I thought maybe a hardware issue, but seeing this I'm convinced its not.  Since I can predict the next outage.  It happens if I am using the machine or not.  I have run memory tests, and passed, disk and cpu tests and they all passed.
I have checked my /etc/cron.hourly directory and it is empty.  I'm not a cron expert or even novice, so I'm curious if there is an issue in there, but I can't tell.
I have checked my logs and can't find errors.
Here is the syslog that is the same around the top of every hour:
Nov 30 13:17:01 saturn CRON[2411]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 30 13:39:01 saturn CRON[2559]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 30 14:02:58 saturn kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov 30 14:02:58 saturn rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="853" x-info="http://www.rsyslog.com"] (re)start
Nov 30 14:02:58 saturn rsyslogd: rsyslogd's groupid changed to 103
Nov 30 14:02:58 saturn rsyslogd: rsyslogd's userid changed to 102
Nov 30 14:02:58 saturn rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Nov 30 14:02:58 saturn kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 30 14:02:58 saturn kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 30 14:02:58 saturn kernel: [    0.000000] Linux version 2.6.32-35-generic-pae (buildd@vernadsky) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #78-Ubuntu SMP Tue Oct 11 17:01:12 UTC 2011 (Ubuntu 2.6.32-35.78-generic-pae 2.6.32.46+drm33.20)
Nov 30 14:02:58 saturn kernel: [    0.000000] KERNEL supported cpus:
Nov 30 14:02:58 saturn kernel: [    0.000000]   Intel GenuineIntel
Nov 30 14:02:58 saturn kernel: [    0.000000]   AMD AuthenticAMD
Nov 30 14:02:58 saturn kernel: [    0.000000]   NSC Geode by NSC
Nov 30 14:02:58 saturn kernel: [    0.000000]   Cyrix CyrixInstead
Nov 30 14:02:58 saturn kernel: [    0.000000]   Centaur CentaurHauls
Nov 30 14:02:58 saturn kernel: [    0.000000]   Transmeta GenuineTMx86
Nov 30 14:02:58 saturn kernel: [    0.000000]   Transmeta TransmetaCPU
Nov 30 14:02:58 saturn kernel: [    0.000000]   UMC UMC UMC UMC


messages looks like this:
Nov 30 13:03:12 saturn kernel: [   43.472394] ppdev: user-space parallel port driver
Nov 30 14:02:58 saturn kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov 30 14:02:58 saturn rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="853" x-info="http://www.rsyslog.com"] (re)start
Nov 30 14:02:58 saturn rsyslogd: rsyslogd's groupid changed to 103
Nov 30 14:02:58 saturn rsyslogd: rsyslogd's userid changed to 102
Nov 30 14:02:58 saturn kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 30 14:02:58 saturn kernel: [    0.000000] Initializing cgroup subsys cpu

I just don't know where else to look to see what might be going on.
If this happened every so often..or about 60 mins after I turned it on I'd think hardware.  I thought it might be hardware for a while.  But if the machine is sitting idle rebooting every hour throughout the night, I think no way that is hardware.  Its just to systematic and predictable.
Any ideas beside hardware as to why this might happen or what I should check?

---

### Post by brianmrowe on 2011-11-30
I think this is fixed now.  I have no idea why it is fixed, but it has stopped rebooting every hour.  I read another post I found which I don't have the link to.
Basically - We had a power outage.  Then this started happening.  From the time after it rebooted and every about hour after that.  I don't know why it was rebooting, but I did what the other person said fixed it for them - they also had their PC shut off because of a power outage.
I shutdown completely, then unplugged the power and turned off the power supply as well.  pulled the plug out of the back and waited a few seconds..  plugged everything back in and rebooted.
Since doing this, no more hourly reboots.  Again, I have no idea why, but the issue has stopped.

---

