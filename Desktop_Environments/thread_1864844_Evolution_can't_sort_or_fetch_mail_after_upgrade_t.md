---
title: "Evolution can't sort or fetch mail after upgrade to 11.10"
date: 2011-10-19
forum: Desktop Environments
---

### Post by pinkunicorn on 2011-10-19
I just got a new computer and installed 11.10 on it, and then copied all the files from my home directory on my previous computer running (I think) 10.04 to it.

After this, Evolution doesn't work as it should. It opens and shows all my old messages, but doesn't fetch new ones from the server. 

Also, it shows the messages with the oldest first instead of the newest as before. When I click the date column to try to change this, it opens a bright orange error message above my mails reading (translated from Swedish) "Error when generating message list no such table mem.INBOX" and leaves the message order as before. Trying to sort using another column gives the same effect.

I have installed all updates available as of just now and restarted the computer after the last round of updates.

---

### Post by pinkunicorn on 2011-10-20
*bump*

---

### Post by jrierab on 2011-10-30
You are not alone. Same thing happens here. The bug has been reported at [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/863960](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/863960)

May be you should subscribe to it, so if more people are affected, a fix could be released sooner.

---

