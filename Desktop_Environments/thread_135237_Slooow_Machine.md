---
title: "Slooow Machine"
date: 2006-02-23
forum: Desktop Environments
---

### Post by reb68 on 2006-02-23
It seems that my PC has slowed way down. I am using KDE3.5 and kubuntu. I looked at the system monitor and it showed 
CPU 90-100%
Memory user 46%
memory Swap 36%
The only thing open is Kmail and Opera.
I have used 82% of disk space. Could that be the cause. I downloaded Netscape a few days ago and could not open it. Is that the cause. I would like to delete it but the only files I find are protected. Thanks for any help.

---

### Post by byen on 2006-02-23
hey red68,
Could you please tell us more about your system specifications?
~byen

---

### Post by racecat on 2006-02-23
Mine's doing the same kind of thing. CPU near 100% all the time, mem climbed to 100% then swap started growing to 100% this A.M. Started noticing disk activity light on when I walk up. Suspect that was managing memory. Tonight I had to do a hard reboot as I got minimal response over half an hour and couldn't shut anything down. Seems okay after reboot (did a software reboot right after the hard one). CPU around 50% and 160 meg mem usage - no swap. Only active apps now are the monitor and 2 windows of Firefox, one with 8 tabs open. Oh, how I love my Session Saver.

Could this be caused by a memory leak? Plan to research what may be causing it. There was nothing in the process table indicating anything like the system load graphs showed, but I'm a believer now.

Bill

---

### Post by reb68 on 2006-02-23
I know I have 256 Memory but do not know much more. Sorry I did do a system log and found the following repeating all day. 
---
02/23/2006 08:50:45 PM	localhost	dhclient	can't create /var/run/dhclient.eth0.leases: Permission denied

02/23/2006 08:50:45 PM	localhost	dhclient	DHCPACK from 192.168.1.254

02/23/2006 08:50:45 PM	localhost	dhclient	DHCPREQUEST on eth0 to 192.168.1.254 port 67

02/23/2006 08:53:13 PM	localhost	dhclient	bound to 65.5.184.154 -- renewal in 142 seconds.

02/23/2006 08:53:13 PM	localhost	dhclient	can't create /var/run/dhclient.eth0.leases: Permission denied

02/23/2006 08:53:13 PM	localhost	dhclient	DHCPACK from 192.168.1.254

02/23/2006 08:53:13 PM	localhost	dhclient	DHCPREQUEST on eth0 to 192.168.1.254 port 67

02/23/2006 08:55:01 PM	localhost	/USR/SBIN/CRON[646]	(debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)

---

