---
title: "[FAILED] operations at startup/shutdown"
date: 2009-06-10
forum: General Help
---

### Post by Entropy_Sam on 2009-06-10
Hi folks,

I'm getting a couple of [FAILED] results for some of my startup operations, and one for my shutdown operations when booting Linux. everything seems to be running fine, if you don't count the fact that running flash in Firefox is guaranteed to cause a complete system freeze within 30 seconds (which I suppose could be related).

I don't really have time to read them at startup/shoutdown as the messages rush by too quickly. I've looked at some of the logs in the Log Viewer, but I honestly don't know where I should be looking to find out what's faled.

Could anyone point me in the right direction as to where I should look to find out which operations aren't executing properly?

---

### Post by hal8000 on 2009-06-10
You need to look through either /var/log/messages or use the Ubuntu log viewer.

When you find a line that has Failed, copy and post it into google, theres usually an answer for most failures, and if not post a small section on the forum.

---

### Post by Entropy_Sam on 2009-06-10
As I said, I looked in the log viewer, but din't know which log to look at...

But thanks for pointing me in the right direction.

---

### Post by hal8000 on 2009-06-10
> **Entropy_Sam said:**
> As I said, I looked in the log viewer, but din't know which log to look at...

But thanks for pointing me in the right direction.

You said you saw Failed somewhere, but didnt say which log.
/var/log/messages is general log file,
/var/log/boot is boot log, this link will help:

[http://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/](http://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/)

---

### Post by Entropy_Sam on 2009-06-10
sorry, I meant the messages flashed by at startup and I didn't have time to read them to find out what had failed - I just saw the word [FAILED]...

---

