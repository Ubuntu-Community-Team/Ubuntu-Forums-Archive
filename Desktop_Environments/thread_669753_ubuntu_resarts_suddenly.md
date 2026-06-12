---
title: "ubuntu resarts suddenly"
date: 2008-01-16
forum: Desktop Environments
---

### Post by uknowho008 on 2008-01-16
Starting this morning ubuntu has restarted randomly twice. i havent changed anything except for installing an update. i cant remember what it was for. anybody having the same problem? i been doing anything but working on my website and browsing the internet. cpu temp is around 25c according to my case temp thing. and hd is at 32c. im not sure how accurate that is but it shouldnt be a problem anyway. thanks.

---

### Post by fwojciec on 2008-01-16
It certainly sounds like a hardware not software problem.  Have you tried opening the case of your computer and cleaning it out a bit with a vacuum cleaner?  I'd also run a memory test just to be sure...

---

### Post by uknowho008 on 2008-01-18
its a pretty new computer so im sure its clean in there. and i also ran a memory test a little while back for 3 days and nothing came up. it hasnt happened again. so my fingers are crossed.

---

### Post by kellemes on 2008-01-18
Have you checked /var/log/messages ?
Often this gives a clue about the issue.

---

### Post by RawMustard on 2008-01-18
when you say restarts, you mean the computer completely reboots?  Or when you login you get taken back to the login screen?

Reason I ask, is because I just downloaded the latest updates to Gutsy and now I can't login, I keep getting taken back to the login window :(

---

### Post by atentik on 2008-03-15
> **RawMustard said:**
> when you say restarts, you mean the computer completely reboots?  Or when you login you get taken back to the login screen?

Reason I ask, is because I just downloaded the latest updates to Gutsy and now I can't login, I keep getting taken back to the login window :(

Having the same problem. Don't know the reason why?

---

### Post by AvalonSpirit on 2008-03-23
> **uknowho008 said:**
> Starting this morning ubuntu has restarted randomly twice. i havent changed anything except for installing an update. i cant remember what it was for. anybody having the same problem?

I've got the same problem. I havent been messing with the system either (just normal update installs).
i'm not sure what im looking for in system log(/var/log/messages),  i get this sort of message in the log at the time it happened

 Mar 22 23:45:01 alonso-desktop syslogd 1.4.1#21ubuntu3: restart.
 Mar 22 23:55:20 alonso-desktop -- MARK --

I dont know, but it could have something to do with it after this Ubuntu stopped recognizing my sound devices which had been working perfectly.
it gives me this error message: No volume control GStreamer plugins and/or devices found.

Any help would be great.
Thanks

---

