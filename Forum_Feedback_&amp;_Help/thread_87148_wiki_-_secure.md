---
title: "wiki - secure?"
date: 2005-11-07
forum: Forum Feedback &amp; Help
---

### Post by mechanic on 2005-11-07
I notice the wiki runs on a secure site. Can't the powers that be sort out the certificate for that site? I keep getting 'certificate can't be verified' messages when I visit. 

BTW this may be the wrong group but I can't find a more appropriate one.

m.

---

### Post by kassetra on 2005-11-07
[quote=mechanic]I notice the wiki runs on a secure site. Can't the powers that be sort out the certificate for that site? I keep getting 'certificate can't be verified' messages when I visit. 

BTW this may be the wrong group but I can't find a more appropriate one.

m.[/quote]

If you mean the official wiki - then you would be correct, we have nothing to do with the official wiki - and ironically enough, you'd have to leave a comment on the wiki to let them know there is a problem.

---

### Post by az on 2005-11-07
They have always used a self-signed certificate.

---

### Post by ubuntu-geek on 2005-11-07
In firefox you can just choose to always accept the cert to bypass future warnings if you wish..

---

### Post by SSTwinrova on 2005-11-07
Hmmm...just thought of something. I'm on XP right now, but have they added themselves to the cert list on the browsers that come with Breezy so that doesn't pop up?

---

### Post by mechanic on 2005-11-08
[QUOTE=ubuntu-geek]In firefox you can just choose to always accept the cert to bypass future warnings if you wish..[/QUOTE]

But the idea of certificates is that they should be traceable to one held by a trusted authority (like Verisign) and they should be current. Bypassing this check means that the security is compromised. If we don't need it why have the wiki on a secure site? If the doc people on Ubuntu can't get this elementary security right, can we trust the Operating System to be secure? It just creates the wrong impression.

m.

---

### Post by az on 2005-11-08
[QUOTE=mechanic]If the doc people on Ubuntu can't get this elementary security right, can we trust the Operating System to be secure? .[/QUOTE]

[http://en.wikipedia.org/wiki/Thawte](http://en.wikipedia.org/wiki/Thawte)
Thawte Consulting is a certificate authority (CA) for X.509 certificates. Thawte was founded in 1995 by Mark Shuttleworth in South Africa and is the second largest public CA on the Internet.

In 1999 VeriSign acquired Thawte in a stock purchase from Shuttleworth for $575 million US dollars and thereby enabled Shuttleworth to become the second space tourist.



[QUOTE=mechanic]
It just creates the wrong impression.

m.[/QUOTE]

I agree.  I think it is a question of the conditions of the sale...

---

### Post by Henrik on 2005-11-11
I agree that it's not ideal ATM. The reason it uses a secure connection though is that the wiki authenticates users at Launchpad, which uses https. If someone were to capture your password when you logged in they would have your Launchpad password, which gives access to all the Ubuntu sites and more. 

However, since the wiki uses a cookie to auto log you in, the secure connection shouldn't be rquired after you've registered. I'll discuss this with the Launchpad people.

---

