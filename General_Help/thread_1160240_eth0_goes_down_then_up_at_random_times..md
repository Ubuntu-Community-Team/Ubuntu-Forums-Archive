---
title: "eth0 goes down then up at random times."
date: 2009-05-15
forum: General Help
---

### Post by 3DLover on 2009-05-15
About 2-3 times a month at seemingly random times, I see kernel messages about eth0 going down and then immediately back up.  Near as I can tell it has never caused a problem, but in the last 12 years of running Linux based servers I have never quite seen this until I built my current server about a year ago.  I was wondering if anyone else out there has seen this?

>uname -a
Linux xxxx.net 2.6.24-22-server #1 SMP Mon Nov 24 20:06:28 UTC 2008 x86_64 GNU/Linux

Tyan Transport GT20 - B2925G20V4H
AMD A64 X2 5000+ 2.6G AM2 2Mb
4 GB Ram

eth0 pluged directly into Business Class 20/20MBit Verizon FIOS

/var/log/syslog:
```

May 15 01:20:02 xxxx snmpd[6938]: Connection from UDP: [127.0.0.1]:42177
May 15 01:20:02 xxxx snmpd[6938]: Connection from UDP: [127.0.0.1]:51447
May 15 01:20:02 xxxx snmpd[6938]: Connection from UDP: [127.0.0.1]:45899
May 15 01:20:02 xxxx snmpd[6938]: Connection from UDP: [127.0.0.1]:38914
May 15 01:20:02 xxxx snmpd[6938]: Connection from UDP: [127.0.0.1]:37696
May 15 01:20:02 xxxx snmpd[6938]: Connection from UDP: [127.0.0.1]:40815
May 15 01:20:02 xxxx snmpd[6938]: Connection from UDP: [127.0.0.1]:48927
May 15 01:20:02 xxxx snmpd[6938]: Connection from UDP: [127.0.0.1]:56643
May 15 01:20:02 xxxx snmpd[6938]: Connection from UDP: [127.0.0.1]:60494
May 15 01:22:36 xxxx kernel: [5872129.649319] eth0: link down.
May 15 01:22:38 xxxx kernel: [5872131.673102] eth0: link up.
May 15 01:22:49 xxxx named[16596]: unexpected RCODE (REFUSED) resolving '10.0-26.106.131.88.in-addr.arpa/PTR/IN': 89.150.192.1#53
May 15 01:22:49 xxxx named[16596]: unexpected RCODE (REFUSED) resolving '10.0-26.106.131.88.in-addr.arpa/PTR/IN': 89.150.224.1#53
May 15 01:22:50 xxxx named[16596]: unexpected RCODE (REFUSED) resolving '10.0-26.106.131.88.in-addr.arpa/PTR/IN': 89.150.192.1#53
May 15 01:22:50 xxxx named[16596]: unexpected RCODE (REFUSED) resolving '10.0-26.106.131.88.in-addr.arpa/PTR/IN': 89.150.224.1#53
May 15 01:25:01 xxxx /USR/SBIN/CRON[17338]: (www-data) CMD (php /usr/share/cacti/site/poller.php 2>&1 >> /var/log/cacti/poller-error.log)
May 15 01:25:47 xxxx named[16596]: unexpected RCODE (REFUSED) resolving '10.0-26.106.131.88.in-addr.arpa/PTR/IN': 89.150.224.1#53
May 15 01:25:47 xxxx named[16596]: unexpected RCODE (REFUSED) resolving '10.0-26.106.131.88.in-addr.arpa/PTR/IN': 89.150.192.1#53
May 15 01:25:47 xxxx named[16596]: unexpected RCODE (REFUSED) resolving '10.0-26.106.131.88.in-addr.arpa/PTR/IN': 89.150.192.1#53
May 15 01:25:48 xxxx named[16596]: unexpected RCODE (REFUSED) resolving '10.0-26.106.131.88.in-addr.arpa/PTR/IN': 89.150.224.1#53

```

Thanks!
-Ray

---

### Post by dcstar on 2009-05-15
> **3DLover said:**
> About 2-3 times a month at seemingly random times, I see kernel messages about eth0 going down and then immediately back up.  Near as I can tell it has never caused a problem, but in the last 12 years of running Linux based servers I have never quite seen this until I built my current server about a year ago.  I was wondering if anyone else out there has seen this?
.......
**eth0 pluged directly into Business Class 20/20MBit Verizon FIOS**
.......

So you can guarantee that an external connection to an ISP keeps working 24x7 365 days a year?

---

### Post by 3DLover on 2009-05-16
> **dcstar said:**
> So you can guarantee that an external connection to an ISP keeps working 24x7 365 days a year?

Nope. I suppose there's some kind of reset going on with the ISP. I was thinking that some kind of process on ubuntu was causing the reset, but it's possible that a reset on the other end is causing this.

---

### Post by dcstar on 2009-05-16
> **3DLover said:**
> Nope. I suppose there's some kind of reset going on with the ISP. I was thinking that some kind of process on ubuntu was causing the reset, but it's possible that a reset on the other end is causing this.

You can test it by unplugging the other side of the link, or pluging the Ubuntu box into an intermediate Ethernet switch.

---

