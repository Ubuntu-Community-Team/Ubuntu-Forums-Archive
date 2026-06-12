---
title: "SSH and SSH_AUTH_SOCK=0 and public/private keys"
date: 2009-06-14
forum: General Help
---

### Post by bonfire89 on 2009-06-14
Hi there,

I recently installed ubuntu server (jaunty) and have been fiddling with ssh and public private keys.

I have been able to successfully connect to the account that was set up during the OS install

However, in order to connect to an account that was made after the install I have to locally enter "SSH_AUTH_SOCK=0" before it will work. If I don't, I receive "Agent admitted failure to sign using the key"

I'm just curious as to why this might be...

Anyone know?

Thanks





Edit:

what do you know, it started working :confused:

regardless, what is the deal with SSH_AUTH_SOCK=0 other people out there have the same issue

---

### Post by narnie on 2010-04-22
I just started messing around with keys on ssh, too. I was having the same problem as you.

I thank you for letting me know about "SSH_AUTH_SOCK=0" as this is allowing me to connect without passwords, as well. 

I, too, am wondering why this is necessary (and why none of the tutorials, including Ubuntu tutorials) don't mention this important step.

Cheerio,
Narnie

---

