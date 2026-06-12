---
title: "time issue"
date: 2005-05-31
forum: Desktop Environments
---

### Post by crash369 on 2005-05-31
hello all.

i don't know why, but ubuntu cannot keep the time right. the clock is too fast and can become as much as 10 minutes off in 48 hours.

turning on auto-synch does not fix the issue.  i've been doing it manually, but that gets quite annoying.

any ideas?

---

### Post by thrift on 2005-05-31
Have you tried using NTP?  This is exactly what this is for.  All my Linux boxes that don't run NTP eventually have their time skew off into oblivion, but installing NTP has fixed it for me.

---

### Post by crash369 on 2005-05-31
yes, that is what i meant by auto-synch.

---

### Post by dyle on 2005-05-31
Are you using Firestarter?  Try and see if setting a policy to allow NTP for outbound connections works for you.  That's what caused my time sync problems.

---

### Post by crash369 on 2005-05-31
no firewall and manual synching via NTP works.

i'm more concerned with the fact that the time changes that much over a very little period, and not with they synching.

---

### Post by thrift on 2005-05-31
Try to find a version of NTP that can be "daemonized" or simply add it to cron.

Time will skew depending on a lot of factors, generally CPU load seems to make a large difference.  Don't be concerned by the fact that it is happening, some of my systems can get off by several days in the matter of a week or so.

To see your cpuload just run uptime from a terminal

If the number on the right are close to 1 or greater, that has a lot to do with why your time is skewing from my experience.

---

