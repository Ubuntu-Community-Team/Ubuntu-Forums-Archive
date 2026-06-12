---
title: "Can't print messages with attachments from Kmail"
date: 2009-05-13
forum: Desktop Environments
---

### Post by ldj on 2009-05-13
After the upgrade to Jaunty, messages with attachments won't print from Kmail to a remote (shared) printer.  No warnings are displayed, just a quiet failure to print.  This worked in Intrepid (according to my wife).  Mail messages without attachments print fine.  The type of attachment doesn't seem to make a difference.

We have two systems (my wife's desktop with a wired connection and my laptop with a wireless connection, both running Jaunty) that both exhibit the problem.  We have two HP printers (HP LaserJet 1320 and HP PSC 2355) attached to my desktop (acting as a household server, running Kubuntu Hardy KDE 3.5.x).  The choice of printer makes no difference regarding the issue.

Printing the "problem" messages to PDF works fine.  So it seems to be some sort of Kmail/CUPS issue, but I'm running out of ideas of where to look or what to try next.

The /var/log/cups/page_log file (on the client machines) for the failed print jobs contains the following:
```
hp1320 ldj 34 [08/May/2009:18:13:06 -0500] 1 1 - localhost
hp1320 ldj 34 [08/May/2009:18:13:28 -0500] total 0 - localhost
```

For successful print jobs, this looks like
```
hp1320 ldj 33 [08/May/2009:18:11:04 -0500] 1 1 - localhost
hp1320 ldj 33 [08/May/2009:18:11:25 -0500] total 1 - localhost
```

The value for "total" varying between 1 (for successful, single page prints) and 0 (for unsuccessful prints) is the only clue I've found.  I didn't see anything that looked unusual in the /var/log/cups/access_log file, and there is no error_log.

Thanks for any ideas or suggestions!

---

### Post by ldj on 2009-09-18
This problem continues on the Jaunty and Karmic installs on my LAN.  The CUPS server is still on an up-to-date Hardy (8.04) system.

Thanks for any suggestions.

    Lowell

---

### Post by krazyd on 2009-09-18
I just tried printing, from kmail, an email with a .doc attached on my HP 1320n and it worked fine. My setup is different though - the printer is connected to my router via ethernet cable and shows up as a network device.

It's a strange problem, and might be something in your CUPS setup. Have you tried asking on the CUPS mailing list?

---

### Post by ldj on 2009-09-19
> **krazyd said:**
> I just tried printing, from kmail, an email with a .doc attached on my HP 1320n and it worked fine. My setup is different though - the printer is connected to my router via ethernet cable and shows up as a network device.

It's a strange problem, and might be something in your CUPS setup. Have you tried asking on the CUPS mailing list?

I suspect it *is* something wrong with my configuration, since no one else is complaining about this issue.  I haven't changed my CUPS setup in several years on the server, and the problem only started when I upgraded the clients to Jaunty (with the default CUPS installation configuration).

Last night, I asked the same question on the CUPS mailing list, so hopefully I'll get some clues there.  What I'm hoping for is some guidance on how to debug/further investigate the problem.  I'd like to know how to see what the client is sending and what the server is receiving.

Thanks for your response, krazyd.

    Lowell

---

