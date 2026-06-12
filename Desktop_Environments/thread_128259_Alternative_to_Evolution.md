---
title: "Alternative to Evolution?"
date: 2006-02-11
forum: Desktop Environments
---

### Post by GrumpyBob on 2006-02-11
Is there a good alternative to the Evolution email system?
I have been trying to persuade Evolution to connect to my work Exchange server, but it seems to be excessively flaky, connection is unreliable, and the Exchange Connector crashes when I try and delete an email or change folder.
I'd quite like to try an alternative.  I installed Thunderbird and Kontact/Kmail, but cannot see options to connect to an Exchange server.
What version of Evolution is in the Dapper repos?  Would that be likely to work with Breezy?

Robert

---

### Post by ebash on 2006-02-11
At work we also have an exchange server. I was able to configure evolution but it started crashing as soon as I changed my windows domain password.

I am quite happy using thunderbird at work, besides I prefer it's simpler interface over Evolution's mess 

**NOTE: ** Thunderbird doesn't support Exchange, but my exchange server supports both POP3 and IMAP. I am using the latter.

At work we also have a web interface for exchange.

Dapper has Evolution  2.5.90-0ubuntu3

---

### Post by GrumpyBob on 2006-02-11
What surprises me is that this is a flagship application.  Are the problems due to subtle changes on the server?

Robert

---

### Post by ebash on 2006-02-11
[QUOTE=GrumpyBob]What surprises me is that this is a flagship application.  Are the problems due to subtle changes on the server?
[/QUOTE]

I don't know exactly what are the problems. But evolution doesn't seem to stable when dealing with exchange. At my work some people couldn't configure evolution at all, even if we were all using the same Ubuntu version.

All that I know is that the exchange is not helping at all. During one of the upgrades of exchange my mailbox became partially corruped. Now everytime that I use thunderbird I always receive illegal headers, although thunderbird still works and I am allowed to read my mail

---

### Post by GrumpyBob on 2006-02-11
Well, I'm going back to using fetchmail to retrieve mail from the IMAP server.  Evolution is so flaky it's useless for dealing with remote mail servers.  Frankly I'm a little astonished that it is so flaky at version 2.4.x.

Robert

---

### Post by biguns on 2006-02-11
For basic stability and functionality you have to admit thats one thing Windows got right. I have resorted to using webmail. I guess I could wipe the dust off my Outlook 2000 and install it on Wine but I have been Windows-less for so long it would feel like wiping your bottom with your other hand, familiar but strange as hell...

---

### Post by cutOff on 2006-02-11
Look at [here]("http://sourceforge.net/search/?words=exchange&type_of_search=soft").

---

### Post by John Jason Jordan on 2006-02-11
I don't need to access an exchange server for e-mail, so I don't know if it would work, but I've been thrilled with Sylpheed. I tried Evolution, but it can't access my three different e-mail accounts individually. And Thunderbird has a bug (still not fixed) where it can't see all the messages on the servers. I also tried Cronos and Kmail, but each had limitations or problems. Finally I found Sylpheed and my life is complete. :)

There is also an extensive list of plugins and scripts for Sylpheed, plus they have an active e-list where you can get quick responses from long-time users.

---

### Post by wastrel on 2006-02-16
I really like Thunderbird - i've used it for IMAP and it works very well.  If you just need email and can talk to your exchange server with IMAP, give Thunderbird a try.

---

