---
title: "what's up with my ntpd?"
date: 2006-01-27
forum: Desktop Environments
---

### Post by twowheeler on 2006-01-27
My syslog is full of these messages:

> localhost ntpd[7259] sendto(2001:5e8:8:19::4): Network is unreachable

It occurs every 17 or 18 minutes.

My /etc/ntp.conf ends with:

> server clock.psu.edu

which is the closest server to my location.  I have no trouble reaching clock.psu.edu, because:

> dan@ubuntu:~$ ping clock.psu.edu
PING otc2.psu.edu (128.118.25.3) 56(84) bytes of data.
64 bytes from otc2.psu.edu (128.118.25.3): icmp_seq=1 ttl=239 time=27.9 ms
64 bytes from otc2.psu.edu (128.118.25.3): icmp_seq=2 ttl=239 time=27.2 ms
64 bytes from otc2.psu.edu (128.118.25.3): icmp_seq=4 ttl=239 time=26.9 ms

Besides, the sendto address in the error message is not formatted like an IP address (2001:5e8:8:19::4).  I can't tell where this is coming from.  Any ideas?

---

### Post by adwait on 2006-01-27
Theres some wierd problem with Ubuntu that does not allow the NTP to sync with the server while booting up even if the network is reachable..........:shrugs:

---

### Post by twowheeler on 2006-01-27
No, this is not a boot problem.  This box hasn't been rebooted for a long time, but it happens every day anyway.

> dan@ubuntu:~$ uptime
 22:12:19 up 5 days, 12:45,  4 users,  load average: 1.47, 1.56, 1.43


---

### Post by dcstar on 2006-01-28
[QUOTE=twowheeler]No, this is not a boot problem.  This box hasn't been rebooted for a long time, but it happens every day anyway.[/QUOTE]
It might be trying to reach an IPv6 address, do a forum search on how to turn off IPv6.

---

### Post by jchau on 2006-04-29
I have a similar problem, except the error is invalid argument.  The errors occur just a frequently.  ](*,) 

Here is one of them:
> localhost ntpd[7489] sendto(132.236.56.250): Invalid argument

My /etc/ntp.conf:
```
# /etc/ntp.conf, configuration for ntpd

# ntpd will use syslog() if logfile is not defined
#logfile /var/log/ntpd

driftfile /var/lib/ntp/ntp.drift
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
#server ntp.your-provider.example


# pool.ntp.org maps to more than 100 low-stratum NTP servers.
# Your server will pick a different set every time it starts up.
#  *** Please consider joining the pool! ***
#  ***  <http://www.pool.ntp.org/#join>  ***
server pool.ntp.org

# ... and use the local system clock as a reference if all else fails
# NOTE: in a local network, set the local stratum of *one* stable server
# to 10; otherwise your clocks will drift apart if you lose connectivity.
fudge 127.127.1.0 stratum 13

# By default, exchange time with everybody, but don't allow configuration.
# See /usr/share/doc/ntp-doc/html/accopt.html for details.
restrict default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1 nomodify

# Clients from this (example!) subnet have unlimited access,
# but only if cryptographically authenticated
#restrict 192.168.123.0  mask  255.255.255.0 notrust

# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet,
# de-comment the next lines. Please do this only if you trust everybody
# on the network!
#disable auth
#broadcastclient

server 127.127.1.0
server clock.psu.edu
server ntp0.cornell.edu
#server ntp.ubuntulinux.org

```

I'd really appreciate any help here. Thanks

---

### Post by bmillsap on 2006-10-29
An old thread, but just noticed that my syslog has the same kinds of messages (the "invalid argument") ones.  This is on Dapper.  Anyone ever find the cause of this?

---

### Post by jazzgossen on 2007-01-05
I'm adding to this old thread too. I have similar problems. 

"grep ntp /var/log/syslog" gives me:
```
Jan  6 00:24:54 undertow ntpd[31359]: can't open /var/log/ntpstats/peerstats.20070105: Permission denied
Jan  6 00:25:59 undertow ntpd[31359]: synchronized to 192.36.143.150, stratum 1
Jan  6 00:25:59 undertow ntpd[31359]: can't open /var/log/ntpstats/peerstats.20070105: Permission denied
Jan  6 00:26:06 undertow ntpd[31359]: can't open /var/log/ntpstats/peerstats.20070105: Permission denied
Jan  6 00:28:02 undertow ntpd[31359]: can't open /var/log/ntpstats/peerstats.20070105: Permission denied
Jan  6 00:28:02 undertow ntpd[31359]: time reset -3.204014 s
Jan  6 00:28:02 undertow ntpd[31359]: couldn't unlink /var/log/ntpstats/loopstats: Permission denied
Jan  6 00:28:02 undertow ntpd[31359]: can't open /var/log/ntpstats/loopstats.20070105: Permission denied
Jan  6 00:28:02 undertow ntpd[31359]: can't open /var/log/ntpstats/peerstats.20070105: Permission denied
Jan  6 00:28:03 undertow ntpd[31359]: can't open /var/log/ntpstats/peerstats.20070105: Permission denied
Jan  6 00:28:44 undertow ntpd[31535]: sendto(192.36.143.151): Bad file descriptor
Jan  6 00:28:45 undertow ntpd[31535]: sendto(82.211.81.145): Bad file descriptorJan  6 00:28:49 undertow ntpd[31535]: sendto(192.36.143.150): Bad file descriptor
Jan  6 00:28:53 undertow ntpd[31535]: sendto(80.240.210.253): Bad file descriptor
Jan  6 00:28:54 undertow ntpd[31535]: sendto(192.36.143.151): Bad file descriptor
Jan  6 00:29:04 undertow ntpd[31359]: can't open /var/log/ntpstats/peerstats.20070105: Permission denied
Jan  6 00:32:22 undertow ntpd[31359]: synchronized to 192.36.143.150, stratum 1
Jan  6 00:32:22 undertow ntpd[31359]: can't open /var/log/ntpstats/peerstats.20070105: Permission denied

```

So the clock does apparently get reset properly, but I also get a flood of error messages. /var/log/ntpstats/peerstats.20070105 (and all other files in that directory) are owned by ntp and have -rw-r--r-- permissions.

The contents of /etc/ntp.conf follow:
```

# /etc/ntp.conf, configuration for ntpd

# ntpd will use syslog() if logfile is not defined
#logfile /var/log/ntpd

driftfile /var/lib/ntp/ntp.drift
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
#server ntp.your-provider.example

server time1.stupi.se

# pool.ntp.org maps to more than 100 low-stratum NTP servers.
# Your server will pick a different set every time it starts up.
#  *** Please consider joining the pool! ***
#  ***  <http://www.pool.ntp.org/#join>  ***
#server pool.ntp.org

# ... and use the local system clock as a reference if all else fails
# NOTE: in a local network, set the local stratum of *one* stable server
# to 10; otherwise your clocks will drift apart if you lose connectivity.
fudge 127.127.1.0 stratum 13

# By default, exchange time with everybody, but don't allow configuration.
# See /usr/share/doc/ntp-doc/html/accopt.html for details.
restrict default kod notrap nomodify nopeer noquery

# Local users may interrogate the ntp server more closely.
restrict 127.0.0.1 nomodify

# Clients from this (example!) subnet have unlimited access,
# but only if cryptographically authenticated
#restrict 192.168.123.0  mask  255.255.255.0 notrust

# If you want to provide time to your local subnet, change the next line.
# (Again, the address is an example only.)
#broadcast 192.168.123.255

# If you want to listen to time broadcasts on your local subnet,
# de-comment the next lines. Please do this only if you trust everybody
# on the network!
#disable auth
#broadcastclient
server ntp.ubuntu.com
server 1.se.pool.ntp.org
server 0.europe.pool.ntp.org
server 2.europe.pool.ntp.org

```

---

### Post by bmillsap on 2007-01-06
In my case, I concluded that ntp was generating the "invalid argument" errors whenever my IP address changed.  I need to restart ntp-server every time my IP changes.

---

