---
title: "Problem with /etc/cron.daily/mysql-server"
date: 2006-06-26
forum: Desktop Environments
---

### Post by gizm0 on 2006-06-26
I'm getting weird error messages from my mysql daily cron jobs:
"Message 4:
From root@localhost Mon Jun 26 06:25:21 2006
Envelope-to: root@localhost
Delivery-date: Mon, 26 Jun 2006 06:25:21
From: root@localhost (Cron Daemon)
To: root@localhost
Subject: Cron <root@Linuxo> test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <LOGNAME=root>
Date: Mon, 26 Jun 2006 06:25:21 +0300

/etc/cron.daily/mysql-server:
/etc/cron.daily/mysql-server: line 50: filename: unbound variable"

I can't figure out what is doing this problem, but mysql works just fine. The mysql-server file attached above.

---

### Post by gizm0 on 2006-07-03
Anybody?:confused:

---

### Post by gizm0 on 2006-07-10
Any solutions?

---

