---
title: "Evolution slow in filtering mail (IMAP)"
date: 2006-11-14
forum: Desktop Environments
---

### Post by pdietric on 2006-11-14
Hi all,

I have set up two filters in Evolution (the version in Edgy Eft) diverting mails to two different folders on the mail server (thus, IMAP not POP3). Additionally, mail is also checked for junk criteria (using spamassassin) and treated accordingly.
Now, I would like to know, if it is normal behavior of Evolution to take approx. 10-15 sec to decide whether, say, 3 messages, which are not very long for that matter, match the filter criteria, and if so, where they should go. It also takes quite some time to "assassinate" a few spam mails.
Of course, because of IMAP, the messages have to be downloaded first. But when I manually download those 3 messages (e.g.) by clicking on them, it doesn't take 10-15 sec altogether.

I would be nice if someone could state whether or not this is ok, and, just in case, provide some helpful hints on how to possibly fix this.

Thank you,

Peter

---

### Post by dcstar on 2006-11-14
> **pdietric said:**
> Hi all,

I have set up two filters in Evolution (the version in Edgy Eft) diverting mails to two different folders on the mail server (thus, IMAP not POP3). Additionally, mail is also checked for junk criteria (using spamassassin) and treated accordingly.
Now, I would like to know, if it is normal behavior of Evolution to take approx. 10-15 sec to decide whether, say, 3 messages, which are not very long for that matter, match the filter criteria, and if so, where they should go. It also takes quite some time to "assassinate" a few spam mails.
Of course, because of IMAP, the messages have to be downloaded first. But when I manually download those 3 messages (e.g.) by clicking on them, it doesn't take 10-15 sec altogether.

I would be nice if someone could state whether or not this is ok, and, just in case, provide some helpful hints on how to possibly fix this.

Thank you,

Peter

Basically, yes. The Spamassassin filtering is pretty slow in my Evolution and by all accounts other people experience a similar situation.

---

