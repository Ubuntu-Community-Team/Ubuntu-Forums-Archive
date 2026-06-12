---
title: "CPU Issues on Dell R300?"
date: 2009-07-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Beoras on 2009-07-16
Hi everyone,
I have a problem on a Dell PowerEdge R300 and I'm out of ideas what to do next.
I'm using Ubuntu Server
> $ cat /proc/version
Linux version 2.6.28-11-server (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009
with Lighttpd, php5-cgi, mysql.
Formerly I used Debian Lenny on a different system (AMD Opteron quadcore with 2,4ghz).

While the AMD System was slower going by its stats, the php parsetimes of the webserver have gone up quite a bit.
When I first had this issue on the AMD System (very bad parsetimes) it was due to a bad cpu scalinggovernor that let the system run on 1,4ghz.
I fixed that by setting /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor to performance which brought parsetimes from 0.1 seconds to around 0.04 Seconds.

Now on the 2,8ghz R300 I have slightly slower parsetimes than on the AMD System.
(Not single parsetimes, I log every php call and its parsetime and they are slightly slower on the average.)

I immediately looked on the same place but I found nothing.
/sys/devices/system/cpu/cpu0/cpufreq doesn't exist!
I tried installing cpufreq-info but I got this:
> $ cpufreq-info
cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Bitte melden Sie Fehler an [email]cpufreq@lists.linux.org.uk[/email].
analysiere CPU 0:
  kein oder nicht bestimmbarer cpufreq-Treiber aktiv
analysiere CPU 1:
  kein oder nicht bestimmbarer cpufreq-Treiber aktiv
analysiere CPU 2:
  kein oder nicht bestimmbarer cpufreq-Treiber aktiv
analysiere CPU 3:
  kein oder nicht bestimmbarer cpufreq-Treiber aktiv
Which basically tells me that I don't have a cpufreq-driver installed or active...
> $ cat /proc/acpi/processor/CPU1/info
processor id:            0
acpi id:                 1
bus mastering control:   yes
power management:        yes
throttling control:      no
limit interface:         no

Now I want to know a few things:
1) is the cpu running at topspeed automatically without throttling control? Can this have an impact on performance?
2) can this problem lead to more dangerous issues in other parts of the system, like general stability?
3) can this slowing down of parsetimes happen because of the switch from debian lenny to ubuntu server?

regards,
Beoras

---

### Post by Beoras on 2009-07-18
*push*

---

