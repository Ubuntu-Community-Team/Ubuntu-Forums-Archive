---
title: "Postfix and Localhost"
date: 2005-05-10
forum: Desktop Environments
---

### Post by Jæd on 2005-05-10
Hi,

I'm having problems with fetchmail and postfix... I seem to have fetchmail setup ok. However I get the following in my logs with some emails:

May 10 20:16:52 localhost postfix/local[28372]: 710FE8F839: to=<me@localhost>, relay=local, delay=0, status=SOFTBOUNCE (mail forwarding loop for me@localhost)

"me" is a valid user name and I've got the following in my main.cf...

mydestination = localhost.localdomain, localhost.localdomain, localhost

I've confirmd this with postconf -n ...

What can be wrong...?

---

### Post by Jæd on 2005-05-10
Ah, I see...

I need to turn off the [b]prepend_delivered_header .

[/b]Setting this to nothing on the host did the trick...

---

