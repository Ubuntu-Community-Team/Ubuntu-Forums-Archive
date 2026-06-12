---
title: "ETQW dies 30 seconds in with lots of players in a server with 9.10 [SOLVED]"
date: 2009-11-02
forum: Gaming &amp; Leisure
---

### Post by Dingo_aus on 2009-11-02
ISSUE NOT SOLVED - please delete this thread as I had to start a new one with a different title as I now know more about the problem (and it isn't [SOLVED] any longer)


Upgraded from 8.10 to 9.10 Karmic Koala (via 9.04).

ETQW used to be rock solid.

Now if I join a server with one or two people it is fine, if I join a server with 24 people it will crash.

My attempted  solution:

Install linux-backports-modules-alsa-karmic 

then start ETQW with this command:

pasuspender /usr/local/games/etqw/etqw -set s_driver oss


...it will crash when there are lots of players on a map.

Often has a moment of texture corruption just before dumping me back to the desktop.

I suspect it might have to do with the number of simultaneous sounds being rendered.

Any ideas on what the cause of the crash is?  Or how to identify if it is because of sounds or graphic drivers etc?

---

