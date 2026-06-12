---
title: "NMap Reports Port 25 open, Shields Up does not"
date: 2006-08-16
forum: Desktop Environments
---

### Post by Koori23 on 2006-08-16
Here's what netstat -tal is telling me:
tcp        0      0 localhost:51368         *:*                     LISTEN
tcp        0      0 localhost:ipp           *:*                     LISTEN
tcp        0      0 *:smtp                  *:*                     LISTEN
tcp        0      0 localhost:59805         *:*                     LISTEN
tcp        0      0 localhost:37672         localhost:51368    ESTABLISHED     
tcp        0      0 localhost:51368         localhost:37672    ESTABLISHED    

NMap tells me that Port 25/smtp is open to the world, I go to GRC.Com and run Shields Up, it reports that it's "stealthed". I even ran Firestarter and then probed JUST the mail ports (25,113 and 143) and saw that Firestarter was correctly reporting the port scan.. I don't get it, I don't have any mail servers connected, I only use webmail, so I don't have any mail apps..

Any answers would be fantastic. Thanks.

Eric

---

### Post by roostishaw on 2006-08-16
I think, but I might be wrong, that if you scanned with nmap using 127.0.0.1 or localhost, it's scanning just your machine, and not running into your router like Shields Up is. This is all true, assuming that you have a router.

---

### Post by jdong on 2006-08-17
tcp 0 0 *:smtp *:* LISTEN


Reports that your system is indeed listening on SMTP on all network interfaces. To fix this, run "sudo dpkg-reconfigure postfix" and choose Local Site (accept other defaults) as the type of delivery.



ShieldsUP is infamously awful as a port scanner, and widely criticized by several security forum communities as being inaccurate and even deceptive at times. Also, if you are behind a router, your port 25 would be guarded.

---

### Post by lupine_nickt on 2006-08-17
Well, the port 25 "might" be guarded. Mine isn't... but that's on purpose :D

Another possibility is that the OP is using an ISP which blocks port 25 by default.

xF,

...Nick

---

### Post by Koori23 on 2006-08-17
> **jdong said:**
> tcp 0 0 *:smtp *:* LISTEN


Reports that your system is indeed listening on SMTP on all network interfaces. To fix this, run "sudo dpkg-reconfigure postfix" and choose Local Site (accept other defaults) as the type of delivery.


Thanks! That seemed to do it.. I did install Mozilla Thunderbird, then uninstalled it a day later.. I'm guessing that might have had something to do with it. Then again, I don't really know for sure.
[B]
Starting Nmap 4.03 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-08-17 20:40 EDT
All 65535 scanned ports on  (69.245.*.*) are: closed[/B]

But, I still see it running as a localhost as netstat -tal shows once again.. Is that supposed to occur? Nmap reports everything is fine, am I reading this incorrectly?

tcp        0      0 localhost:51368         *:*                     LISTEN
tcp        0      0 localhost:ipp           *:*                     LISTEN
tcp        0      0 localhost:smtp          *:*                     LISTEN
tcp        0      0 localhost:59805         *:*                     LISTEN
tcp6       0      0 ip6-localhost:smtp      *:*                     LISTEN

---

### Post by jdong on 2006-08-18
It may not be your fault. Sometimes an upgrade will screw up configuration a bit, or something like that since I've actually seen this situation on one of my heavily modified, Breezy->Dapper updated boxes. I'm currently blaming myself for it, as my other similarly managed Breezy->Dapper boxes didn't have the port open!

---

