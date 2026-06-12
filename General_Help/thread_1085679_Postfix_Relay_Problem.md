---
title: "Postfix Relay Problem"
date: 2009-03-03
forum: General Help
---

### Post by dstu69 on 2009-03-03
Hello,

We setup postfix on Ubuntu 7.10 server with mysql virtual domains and mailboxes and practucally everything works fine, except for mail relay issues.

Spammers managed to connect to our server and sent more than 50,000 messages in a few hours. I had to block in the firewall port 25 inside and out completely and we're not getting any emails until it's resolved.

We defined 2 subnets from which emails should be allowed and I also want to allow authenticated users to send from anywhere, but except for that, no emails should be sent by the server.

I'm attaching the main.cf and master.cf files.

This is what the server answers when connecting to port 25:
> 220 mail.mydomain.com ESMTP Server
ehlo
502 5.5.2 Error: command not recognized
ehlo david
250-mail.mydomain.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN


Can anyone help me, please? It's very urgent.

Thanks,

David

---

