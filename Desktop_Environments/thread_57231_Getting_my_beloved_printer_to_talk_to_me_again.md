---
title: "Getting my beloved printer to talk to me again"
date: 2005-08-15
forum: Desktop Environments
---

### Post by tag on 2005-08-15
When I initially installed ubuntu, i set up cups and my Samsung ML-1410 in a whiff. It all worked fine and I forgot about it, since I don't use my printer every day. Now that I've been using Ubuntu for 2 months, I wanted to use the printer again, but it doesn't work. I never touched the printer configuration again since back then, but this is what i get from a tail -f /var/log/cups/error_log now:

I [16/Aug/2005:00:03:04 +0200] Adding start banner page "none" to job 7.
I [16/Aug/2005:00:03:04 +0200] Adding end banner page "none" to job 7.
I [16/Aug/2005:00:03:04 +0200] Job 7 queued on 'SAMSUNG_1410' by 'tag'.
E [16/Aug/2005:00:03:04 +0200] Unable to convert file 0 to printable format for job 7!
I [16/Aug/2005:00:03:04 +0200] Hint: Do you have ESP Ghostscript installed?
I [16/Aug/2005:00:03:04 +0200] Hint: Try setting the LogLevel to "debug".

I don't have a clue what's going on there. but gs-common,gs-esp and gs-gpl are all installed. Setting the loglevel to debug doesn't reveal anything interesting. What is that?

---

