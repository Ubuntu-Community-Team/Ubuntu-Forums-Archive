---
title: "How to configure GTALK via PIDGIN?"
date: 2009-06-22
forum: General Help
---

### Post by volanin on 2009-06-22
Hello.
How do I configure GTALK on PIDGIN?
I have a google account, but no gmail or any other google services.
This google account is: **gtalk@example.com** (Domain hidden to avoid SPAM).


I am doing this:

**Protocol**: XMPP
**Username**: gtalk
**Domain**: example.com
**Resource**:
**Password**: ********


The Advanced tab has this:

**Require SSL/TLS**: YES
**Force old (port 5223) SSL**: no
**Allow plaintext auth over unencrypted streams**: no

**Connect Port**: 5222
**Connect Server**: talk.google.com
**File Transfer Proxies**: proxy.jabber.org


But trying to connect with these settings gets me the message:

[b]gtalk@example.com/ disabled
Not Authorized[/b]


What am I doing wrong?
Thank you!
:)


*P.S.: Using PIDGIN 2.5.7 from GETDEB.NET on Jaunty 64-bit*

---

### Post by Therion on 2009-06-22
[http://www.manast.com/2007/05/11/how-to-configure-pidgin-to-work-with-google-talk/](http://www.manast.com/2007/05/11/how-to-configure-pidgin-to-work-with-google-talk/)

---

### Post by geirha on 2009-06-22
Did you follow this? [http://www.google.com/support/talkgadget/bin/answer.py?hl=en&answer=24073](http://www.google.com/support/talkgadget/bin/answer.py?hl=en&answer=24073)

---

### Post by volanin on 2009-06-22
**@Therion:**
Thank you, but the configuration there requires a gmail.com based google account, and mine is not from the gmail.com domain. Also, the configuration suggested in the Advanced Tab results in connection errors.

**@geirha:**
Yes, indeed I tried. The pidgin in the google setup page is an old version, but if I do exactly as they say (and do not touch the Advanced tab at all), all I get is Stream Error.


Any other suggestions?

---

### Post by salvachn on 2009-06-22
I use a domain different from gmail.com and it works perectly fine with pidgin! Only file transfers don't work, but it is a g-talk wide problem.

---

### Post by volanin on 2009-06-22
> **salvachn said:**
> I use a domain different from gmail.com and it works perectly fine with pidgin! Only file transfers don't work, but it is a g-talk wide problem.

Oh please.
Can you write your configuration, or post screenshots of the account configuration window here?

---

### Post by volanin on 2009-06-22
bump?

---

### Post by khc on 2009-06-22
configure SRV record for your domain.

---

### Post by volanin on 2009-06-22
That was exactly it!
Thank you.

---

