---
title: "Dell Inspiron 15 3521 : Having problems with Ubuntu OS"
date: 2014-01-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ps14003 on 2014-01-12
I just bought a new Dell Inspiron 15 3521 with Ubuntu 12.04 LTS preloaded. Now I am having a few problems with my OS which I am listing as following 1. Whenever I hibernate the system and restart it later, I get a blank screen.   2. On restarting the system, sound is muted by  default.   3. I had Dell Recovery Image stored on my USB Pen drive. Now suddenly, the OS refuses to recognize the pendrive when i plug it in.   4. Plus, while operating the system, if my wired broadband connection breaks and the restarts, it refuses to recognize it as such. I need to restart the system.   Can anyone suggest me a stable solution?

---

### Post by mikewhatever on 2014-01-12
Hi, and welcome to the forums:
1. Hibernation (aka suspend to disk) is unreliable, so much so, that it's disable in Ubuntu by default. Someone at Dell must have thought it a good idea to enable it, apparently without any QA. You are welcome to file a bug report.
2. Another rather common problem - here's a possible solution->[http://www.webupd8.org/2009/06/sound-muted-after-restart-in-ubuntu.html](http://www.webupd8.org/2009/06/sound-muted-after-restart-in-ubuntu.html).
3. Not sure what you mean by "refuses to recognize". More details needed.
4. Same as 3.

---

