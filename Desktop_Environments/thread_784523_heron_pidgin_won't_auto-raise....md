---
title: "heron: pidgin won't auto-raise..."
date: 2008-05-06
forum: Desktop Environments
---

### Post by dwhsix on 2008-05-06
I could have sworn in an earlier version of Ubuntu I was able to get pidgin to auto-raise on a new message... that is, if someone started an IM with me, the message window would pop up.  It's not working now, and is a pain because I frequently miss IMs.

Is this is the base pidgin preferences?  I couldn't find it anywhere... I also tried "Raise conversation window" in the Message Notification plugin, with no luck.

Thoughts?

Thanks!  dwh

---

### Post by meran99 on 2008-05-08
Hi, it looks like you need to install "pidgin-libnotify";

$ sudo aptitude install pidgin-libnotify

Then enable the plugin.

Andrew.

---

