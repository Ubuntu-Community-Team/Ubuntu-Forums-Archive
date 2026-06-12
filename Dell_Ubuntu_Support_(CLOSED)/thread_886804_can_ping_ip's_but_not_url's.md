---
title: "can ping ip's but not url's"
date: 2008-08-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hockeybud64 on 2008-08-11
I am running edubuntu on a Dell GX270.
I am having a problem getting the dns to resolve url's.
I can ping ip's and get a response, but can not ping url's.
Any thoughts?

---

### Post by Belarios on 2008-08-11
Whatcha got in /etc/resolv.conf?  It should be something like 
```
nameserver 192.168.0.1
```
if you're behind some kinda gateway/router.

---

### Post by RedRat on 2008-08-13
> **hockeybud64 said:**
> I am running edubuntu on a Dell GX270.
I am having a problem getting the dns to resolve url's.
I can ping ip's and get a response, but can not ping url's.
Any thoughts?
Some URLs have turned off the ping return command. I believe, for example, that Microsoft.com did this 4 or 5 years ago. Most felt it was a nuisance. 

I can ping ubuntuforums.org but not microsoft.com. Try the ubuntu ping.

---

