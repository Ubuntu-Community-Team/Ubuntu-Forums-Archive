---
title: "evolution 2.4.1 does no longer save a copy of sent messages"
date: 2005-11-22
forum: Desktop Environments
---

### Post by piecom on 2005-11-22
After upgrading to Ubuntu 5.10/Evolution 2.4.1 sent messages are no longer saved in the designated directory neither in /INBOX/Sent nor in /Sent if specified like that. I already tried IMAP and IMAP4Rev1 with no result. This worked in the previous version of Evolution with no problems. I have to force Evolution to send a copy of each message to my own email adress and afterwards move it from INBOX to /INBOX/sent.

Any hints appreciated.

---

### Post by dcstar on 2005-11-22
[QUOTE=piecom]After upgrading to Ubuntu 5.10/Evolution 2.4.1 sent messages are no longer saved in the designated directory neither in /INBOX/Sent nor in /Sent if specified like that. I already tried IMAP and IMAP4Rev1 with no result. This worked in the previous version of Evolution with no problems. I have to force Evolution to send a copy of each message to my own email address and afterwards move it from INBOX to /INBOX/sent.

Any hints appreciated.[/QUOTE]
I assume you are specifying the directory in the particular Mail Account area?

Also, check that you don't have a "Find Now" filter accidentally set for your Sent folder (right click that folder and check the Properties to look at the Message Count).

---

### Post by piecom on 2005-11-23
Thanks for the hints.
[QUOTE=dcstar]I assume you are specifying the directory in the particular Mail Account area?
[/QUOTE]
yes
[QUOTE=dcstar]
Also, check that you don't have a "Find Now" filter accidentally set for your Sent folder (right click that folder and check the Properties to look at the Message Count).[/QUOTE]
no filters active, otherwise I wouldnt see the copies I recieve and move manually to the designated directory.

As I am a german user, maybe the problem is related to the language settings resp. the only partial translation of version 2.4.1 of evolution, handling of character sets or german umlauts. (evolution settings say, it tries to access the imap subdirectory as 'INBOX/Sent' resp. the system directory 'Sent' although its displayed - and may be internally represented - as 'Eingang/Sent' resp. 'Verschickt'.

So, still any hint welcome.

---

### Post by piecom on 2005-11-23
[QUOTE=piecom]

no filters active, otherwise I wouldnt see the copies I recieve and move manually to the designated directory.[/QUOTE]

Sorry, I missed the point. There was an outgoing filter active filtering virus mails. As the f-prot installation directory was no longer valid (changed by upgrade from previous installation) all outgoing mail was moved to the virusmail folder. But all outgoing mail was sent, too.

Doesnt evolution stop processing mails after moving them to another folder because of virus or spam content? It seems local virus filtering doesnt work after upgrade at all (tested with eicar)!!!

So my actual problem is solved. But it has turned out to be a far bigger problem to follow in another thread.

Thank you for your attention.

---

### Post by abeowitz on 2005-12-12
I've had a similar problem.  It seems whenever I open the settings for the exchange account, the default "sent" and "drafts" folders go blank.  Outgoing mail ends up in my inbox.

So, there's definitely a bug in storing those settings.

---

### Post by lferree on 2008-07-09
I have the same problem.  Sent messages aren't being saved.  What's worse, messages that were saved in the Sent folder are now missing.

After scouring the Internet, I see no solutions and terribly regret using Ubuntu for anything more than a test platform.  As much as I don't want to go back to Winblows, I can't afford to lose any more of my company's data.

---

### Post by lferree on 2008-07-09
OMG!  Do I feel terribly dumb and relieved.

MAKE SURE A SEARCH FILTER ISN'T ENABLED.


Hope this helps someone else and I don't lose any Cups of Ubuntu.  LOL

Sorry.

---

