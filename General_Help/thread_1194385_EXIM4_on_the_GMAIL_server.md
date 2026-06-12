---
title: "EXIM4 on the GMAIL server"
date: 2009-06-22
forum: General Help
---

### Post by kbb139 on 2009-06-22
Hi,
I`m trying to setup smart host using the gmail server (smtp.gmail.com), my gmail email as username and exim4.
When I try it with telnet this is what I get:


root@kbbpc:/home/kbb# telnet smtp.gmail.com 25
Trying 72.14.221.111...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP l19sm10237787fgb.11
helo router
250 mx.google.com at your service
mail from: [EMAIL="xavelus@gmail.com"]xavelus@gmail.com[/EMAIL]
[COLOR=Red]530 5.7.0 Must issue a STARTTLS command first. l19sm10237787fgb.11[/COLOR]

What is TLS and how to set it up?

---

### Post by blackxored on 2009-06-22
It's some sort of authentication like SSL and the like.  You must use TLS with exim, so you'll need to configure it to use secure authentication.

---

### Post by kbb139 on 2009-06-22
It is said in the tutorial: "Also check off "TLS" under "Use secure connection."

How can I set it? I`m configuring mail server for the first time...

---

