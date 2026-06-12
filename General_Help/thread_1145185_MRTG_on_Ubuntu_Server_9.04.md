---
title: "MRTG on Ubuntu Server 9.04"
date: 2009-05-01
forum: General Help
---

### Post by b.ng on 2009-05-01
Having a testing server running Ubuntu Server 9.04 with MRTG and Smokeping installed. I found keep receiving the same email from the root, and the content is as follow:

& 
Message 6:
From root@svr01 Thu Apr 30 23:50:22 2009
Envelope-to: root@svr01
Delivery-date: Thu, 30 Apr 2009 23:50:22 +0800
From: root@svr01 (Cron Daemon)
To: root@svr01
Subject: Cron <root@svr01> if [ ! -d /var/lock/mrtg ]; then mkdir /var/lock/mrtg; fi; if [ -x /usr/bin/mrtg ] && [ -r /etc/mrtg.cfg ]; then env LANG=C /usr/bin/mrtg /etc/mrtg.cfg 2>&1 | tee -a /var/log/mrtg/mrtg.log ; fi 
Content-Type: text/plain; charset=UTF-8
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>
Date: Thu, 30 Apr 2009 23:50:11 +0800

ERROR: I Quit! Another copy of mrtg seems to be running. Check /etc/mrtg.pid
Daemonizing MRTG ...

As far as I know Smokeping do not required MRTG, so is there something wrong with my installation?

Could someone here help? Many thanks.

---

