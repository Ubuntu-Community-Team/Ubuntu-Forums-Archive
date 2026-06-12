---
title: "Evolution, Exchange and server rules problem"
date: 2007-05-03
forum: Desktop Environments
---

### Post by sarnaud on 2007-05-03
Hi

I'm testing the possibility of free software for my company, and I'm running into a strange problem with evolution and exchange.

The software are :
* Evolution 2.10.1
* Evolution-exchange 2.10.1

* Exchange 2000 (6.0.6249.0) on Windows 2000 server

Everything works ok, but one small thing. If I write an email to someone that has set is "away" status, or has set up a rule to transfer his/her emails to another mailbox, then my mail es reposted to the original To and CC, instead of just me, or to the external address.

For example, user A with email [email]foo@bar.com[/email], has a rule on the exchange server server to transfer a copy to [email]user@home.com[/email].
If I write an email to him, or a group he belongs to, let's say [email]commercial@bar.com[/email], then my mail is posted again with :
From: [email]foo@bar.com[/email]
To: [email]user@home.com[/email]

but it is delivered to [email]commercial@bar.com[/email].

Here follows the full headers from the message, that is delivered to the wrong mailbox.

X-MimeOLE: Produced By Microsoft Exchange V6.0.6249.0
Received:  from WORKSTATION by EXCHANGESERVER; 03 May 2007 14:24:46 +0200
MIME-Version: 1.0
Content-Type: text/html; charset="utf-8"
Content-Transfer-Encoding: base64
content-class: urn:content-classes:message
Subject: TR : test
Date: Thu, 3 May 2007 14:24:46 +0200
Message-ID: <786B6B320D873C4ABFB7559E60E4032684AA0F@exchangeserver.domaine>
X-MS-Has-Attach: 
X-MS-TNEF-Correlator: 
Thread-Topic: test
Thread-Index: AceNfgl6Cjvi4+McTxOIg3VmsXMYwQAAAAMa
From: [email]foo@bar.com[/email]
To: [email]user@home.com[/email]
X-Evolution-Source: exchange://mylogin;auth=NTLM@EXCHANGESERVER/

Anyone has an idea why it does this ?

---

### Post by sarnaud on 2007-05-04
Another solution would be not to use exchange directly to send emails, but through SMTP. It seems this option was available in previous versions, but I don't see it with 2.10.1.

Is there any way to use a SMTP server to send mails, instead of exchange ?

---

