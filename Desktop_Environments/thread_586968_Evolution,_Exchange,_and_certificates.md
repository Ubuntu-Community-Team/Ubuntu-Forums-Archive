---
title: "Evolution, Exchange, and certificates"
date: 2007-10-22
forum: Desktop Environments
---

### Post by negiscallion on 2007-10-22
In short, I am no longer able to use evolution to talk to the Exchange 2003 server at my company despite having done so for quite a long time. 

My suspicion is that this problem has to do with certificates having been added to the SSL connection through which the Exchange WebDav is hosted. I am linking the cessation of usability to the SSL certificates because: 1) this problem is happening on both my machine and that of a co-worker, 2) neither of us had touched our evolution configuration is a while and 3) the sys. admin installed the certificates shortly before the problems started occurring. I am, however, not 100% certain of the cause. Any help in fixing this problem or further diagnosing it would be be greatly appreciated.

The exact symptom seems to to be an inability to authenticate with the WebDav interface. I am guessing that the exchange plug-in is either failing to correctly parse the input web form or is sending garbage back to it. Enabling debugging in evolution produces the following output (snipped to only include the relevant portion):

```

GET /exchweb/bin/auth/owalogon.asp?url=https://[servername]/exchange/&reason=0 HTTP/1.1
E2k-Debug: 0x8920658 @ 1192716240 [restarted]
Host: [servername]
Authorization: [snip]
User-Agent: Evolution/1.12.0

7 Connection terminated unexpectedly
E2k-Debug: 0x8920658 @ 1192716240

```

The message "Connection terminated unexpectedly" is quite unexciting. 

Both of us are running gutsy which includes evolution 2.12 and evolution-exchange 1.12. Thank you in advance.

---

### Post by negiscallion on 2007-10-31
* bump *

---

