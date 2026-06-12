---
title: "Evolution Configuration problems with Verizon DSL"
date: 2009-06-22
forum: General Help
---

### Post by wanderingarticfox on 2009-06-22
I located a lot of my settings in my windows OS for my Verizon account but I am having trouble configuring Evolution with this data:
Domain: dsl.verizon.net
Network Protocol: TCP/IP
POP3: incoming.verizon.net
SMTP: outgoing.verizon.net
SSL: 3.0
TLS: 1.0
NNTP[news]:  news.verizon.net
[http://www.verizon.net/central/vzc.portal](http://www.verizon.net/central/vzc.portal)
](*,)
I did not locate the Port numbers and think that could be the problem but I could use advice from anyone familiar with Evolution and changing the settings for a non-free email account.

I do have verizon as my homepage in Firefox and of course use the mail feature there.  I do not want to use Outlook Express as an intermidiate because I want to fire MS and just Ubuntu with my new build in Sept.

I have not enabled the add-on 'FoxyProxy' as of yet but I have it downloaded and installed into Firefox; looked like a potential tool for determing Ports but I'm a neewbie:confused:

---

### Post by michy99 on 2009-06-22
In Evolution, go to Edit->Preferences. Choose Mail Account and click Add. In the Identity tab, put a name for the account, your full name, and email address. 

In Receiving Email tab, choose POP, put incoming.verizon.net for server, fill in your username (for example, if your email is [email]joe@verizon.neet[/email], your username is joe), If you need a password to log in, then choose password under Authentication Type, and check Remember Password.

In Sending Email tab, choose SMTP, put outgoing.verizon.net in server. Put PLAIN under Authentication.

I think this is all you need, unless you want to use it for newsgroups.

---

### Post by wanderingarticfox on 2009-06-22
OK can you help me with this error meesage when I went to send/receive I got this:

Error while performing operation.

Failed to connect to SMTP server outgoing.verizon.net in secure mode: STARTTLS not supported

Failed to connect to SMTP server outgoing.verizon.net in secure mode: STARTTLS not supported

:confused::confused:

---

### Post by wanderingarticfox on 2009-06-22
> **wanderingarticfox said:**
> OK can you help me with this error meesage when I went to send/receive I got this:

Error while performing operation.

Failed to connect to SMTP server outgoing.verizon.net in secure mode: STARTTLS not supported

Failed to connect to SMTP server outgoing.verizon.net in secure mode: STARTTLS not supported

:confused::confused:

I change to no encrytion will try to send something; wait one:)

---

### Post by wanderingarticfox on 2009-06-22
Thanks Michy99, That fixed things:) I think I was making things more compicated than I needed. Man Has MS ruined me and I'm so happy to be able to say I Ubuntu:o


By the way how do I mark this 'solved' so others can find it?

---

### Post by leonardo_neo on 2009-06-22
Bottom right side of the page, you will find "edit tags". Select that, and then write SOLVED.

:)

---

### Post by gfd_2 on 2011-11-23
Thanks for the info! I was having no luck changing the settings, I deleted the initial account then re-created it following your instructions and it's working.

---

