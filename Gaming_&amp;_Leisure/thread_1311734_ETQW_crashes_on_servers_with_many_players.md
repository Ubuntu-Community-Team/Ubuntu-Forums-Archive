---
title: "ETQW crashes on servers with many players"
date: 2009-11-02
forum: Gaming &amp; Leisure
---

### Post by Dingo_aus on 2009-11-02
Upgraded from 8.10 to 9.10 Karmic Koala (via 9.04).

ETQW used to be rock solid. Not any longer - crashes in servers with lots of people playing.

Now if I join a server with one or two people it is fine, if I join a server with 24 people it will crash.

My attempted  solution:

Install linux-backports-modules-alsa-karmic 

then start ETQW with this command:

pasuspender /usr/local/games/etqw/etqw -set s_driver oss


...it will crash when there are lots of players on a map.

ETWQ often has a moment of texture corruption on screen just before dumping me back to the desktop.

I suspect it might have to do with the number of simultaneous sounds being rendered.

Any ideas on what the cause of the crash is?  Or how to identify if it is because of sounds or graphic drivers etc?

---

### Post by Dingo_aus on 2009-11-03
looking at my /var/log/messages after the crash reveals:

Nov  3 20:10:20 Tyr pulseaudio[2473]: ratelimit.c: 132 events suppressed


This leads me to think the crash is being caused by a pulseaudio bug.

Seems to be an issue with the latest kernel, going to try another one and will report results

---

### Post by Dingo_aus on 2009-11-03
The problem was in ~/.etqwcl

I just needed to delete this folder and everything worked fine once again

---

