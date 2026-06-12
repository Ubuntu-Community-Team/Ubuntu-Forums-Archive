---
title: "Can't *send* emails in Thunderbird."
date: 2009-06-19
forum: General Help
---

### Post by XtinaS on 2009-06-19
I'm using Hardy and Thunderbird.  I have two accounts, with two different outbound-mail servers set up.  They are both IMAP, with incoming server set to port 143 and outgoing to port 25.

My issue is that I cannot send emails, from either account.  I can receive emails just fine, but when I try to send emails, I get an error saying that connecting to the SMTP server [server] failed.

I can't tell if it's a port issue or not.

Where do I start, or what do I do?

---

### Post by paperplate9 on 2009-06-19
try telnet'ing to the smtp server on 25

---

### Post by virgoboy on 2009-06-21
I am having this same issue with Evolution.  'paperplate9', could you please explain your answer/solution a bit further?  Thanks in advance!!

---

### Post by JordyD on 2009-06-21
> **virgoboy said:**
> I am having this same issue with Evolution.  'paperplate9', could you please explain your answer/solution a bit further?  Thanks in advance!!

Open a terminal, type "telnet <name of server> 25".

For example, for Gmail you would type:
```
telnet smtp.google.com 25
```

---

### Post by virgoboy on 2009-06-21
Here is what i got:

telnet smtpauth.earthlink.net 25
Trying 207.69.189.201...
Connected to smtpauth.earthlink.net.
Escape character is '^]'.
220-elasmtp-mealy.atl.sa.earthlink.net ESMTP Exim 4.67 #1 Sun, 21 Jun 2009 17:02:30 -0400
220-NO UCE.  EarthLink does not authorize the use of its computers or network
220 equipment to accept, transmit, or distribute unsolicited e-mail.

---

### Post by virgoboy on 2009-06-23
Nevermind- got it to work now! :P

---

