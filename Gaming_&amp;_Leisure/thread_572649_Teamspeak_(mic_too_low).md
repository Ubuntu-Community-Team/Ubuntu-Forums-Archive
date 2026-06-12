---
title: "Teamspeak (mic too low)"
date: 2007-10-10
forum: Gaming &amp; Leisure
---

### Post by WeeDsk1lL on 2007-10-10
Hi
I have already searched the forums here, but i found nothing concerning my problem.
I got TS installed, i also can join servers and hear, but the others say, that they can barely hear me.
In the TeamSpeak settings i have activation at whisper and output on shout.  In my Sound preferences i got the mic on 100%.
So what do i have to do about this ALSA/OSS thing, cause iam quite sure it depends on that somehow.

Greetz
WeeDsk1lL

---

### Post by fng on 2007-10-13
You should enable mic boost (+20) in alsamixer

sudo apt-get install alsa-utils
or
sudo apt-get install alsamixergui

---

