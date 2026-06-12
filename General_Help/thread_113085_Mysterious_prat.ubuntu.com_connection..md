---
title: "Mysterious prat.ubuntu.com connection."
date: 2006-01-05
forum: General Help
---

### Post by Nameeater on 2006-01-05
I did netstat -ap and I got this:

tcp     1448      0 210-246-6-136.para:2181 prat.ubuntu.com:www  ESTABLISHED 7308/http

And when you visit that box's webpage you get "It works!" which isn't very reassuring. I then grep'd for http and find 3 processes in total, but only one showing as having a connection in netstat.

I only had Opera and a terminal window running, none of the webpages were about or featured Ubuntu and after a couple of minutes the processes disappear.

What is this process, and what is that prat.ubuntu.com box?

---

### Post by bonzodog on 2006-01-05
From what i can determine, it's part of the ubuntu trace project, though what this project actually is doing, i'm not sure of.

---

### Post by jdong on 2006-01-05
archive.ubuntu.com is run on a round-robin rotation, currently between two servers: prat and syowa.

If you ping archive.ubuntu.com, you'll see the output alternate between:

```

PING archive.ubuntu.com (82.211.81.151) 56(84) bytes of data.

```
(note how this IP matches with prat.ubuntu.com)
and
```

PING archive.ubuntu.com (82.211.81.182) 56(84) bytes of data.

```


In the background, the /etc/cron.daily/apt script is used to run an elaborate 'apt-get update' so that update-manager can track updates. You're just seeing this in action through netstat. Since it's just an apt-get update, the operation is very quick and will disappear.

The rotation servers use Apache virtual hosts, so they respond differently based on what hostname your browser (or apt-get) claims it used to obtain its IP. Even though they resolve to the same IP, archive.ubuntu.com and prat.ubuntu.com are TWO COMPLETELY DIFFERENT concepts to the web server.

---

### Post by bonzodog on 2006-01-05
And here was me disabling cron after thinking it wasn't running anything, followed that guide on speeding up breezy.

---

