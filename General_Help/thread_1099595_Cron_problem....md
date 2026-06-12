---
title: "Cron problem..."
date: 2009-03-18
forum: General Help
---

### Post by Kareeser on 2009-03-18
I've been getting these in local mail for awhile now... it seems to have started when I installed hostsdeny, but at the same time, I also enabled cron logging... so I don't know what the problem is...

In any case:
```
Subject: Cron <root@server-3> test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
Content-Type: text/plain; charset=UTF-8
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <LOGNAME=root>

/etc/cron.daily/man-db:
find: .: Permission denied

```

Any clue what this cryptic message means?

---

### Post by Kareeser on 2009-03-28
Bumpasaurux Rex! Ahhhh!

---

